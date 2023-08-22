# angular_version_update
Here are steps and some issues with solving that you could find when will try to update Angular version (help to update from 6.x to 11.x)

Changes regarding Angular 11 works properly with node -v 14.15.0

0) First of all check https://update.angular.io/ and try to follow. Of course it will not provide all steps and issues for your specific case.

Here are the steps and issue solving that might also help:

1) Update you glocal angular cli version
2) Temporary cut packages that use Angular as a dependecy
3) Update angular versions via `ng update` cli command
4) Check and compare changes in project with https://update.angular.io/
5) Move back cutted packages to package.json and update it according of angular vesion

6) Migrate usages of @Effect decarator to createEffect() (execute "ng generate @ngrx/schematics:create-effect-migration")
7) Update types in generic ramda methods (you will have compilation errors otherwise)
8) Remove "keyofStringsOnly": true and add "skipLibCheck": true in the tsconfig.json
9) Update karma.conf.js to use 'karma-coverage' instead of 'karma-coverage-istanbul-reporter'
10) If you have exclude conditions for assets in angular.json, it should be removed and changed by replaced images from project
root path
11) Start build script and fix errors in production mode\
-- In case you see `An error was thrown in afterAll
  Uncaught TypeError: jasmine.QueryString is not a constructor
  TypeError: jasmine.QueryString is not a constructor` - thats mean you need to directly install 
jasmine-core package version 4.1.0
12) Run npm run lint and npm run test, fix deprecation warnings if appeared
13) issue with font url on prod build
14) Issue with abstract class @Injectable decorator in prod build

update tslint to eslint:
use\
https://github.com/angular-eslint/angular-eslint#migrating-an-angular-cli-project-from-codelyzer-and-tslint
