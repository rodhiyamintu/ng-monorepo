
# Angular Micro Frontend Application

- [Angular Micro Frontend Application](#angular-micro-frontend-application)
  - [Generate Application](#generate-application)
  - [Native Federation](#native-federation)
  - [Add Into Host Application](#add-into-host-application)
  - [Add Into Remote Application](#add-into-remote-application)
  - [Add Routes into shell](#add-routes-into-shell)


```shell
ng new my-workspace --create-application=false
```

## Generate Application
```shell
ng generate application shell --prefix app-shell
ng generate application todo --prefix app-todo
```

## Native Federation
```shell
npm i -D @angular-architects/native-federation
```

## Add Into Host Application
```shell
ng g @angular-architects/native-federation:init --project shell --port 4200 --type dynamic-host
```
## Add Into Remote Application
```shell
ng g @angular-architects/native-federation:init --project todo --port 4201 --type remote
```

## Add Routes into shell
```ts
export const routes: Routes = [
  { path: '', component: HomeComponent },
  {
    path: 'todo',
    loadComponent: () =>
      loadRemoteModule('todo', './Component').then((m) => m.AppComponent),
  },
  {
    path: '**',
    component: HomeComponent,
  },
];
```

