# Setup Bootstrap5 with Django
## source:
- https://www.npmjs.com/package/gulp-sass
- https://zellwk.com/blog/dart-sass-gulp/

## Steps
 - npm install --global gulp-cli (if gulp not installed)
 - npm init
 - npm install gulp sass gulp-sass gulp-sourcemaps  --save-dev
 - npm install bootstrap
 - create gulpfile.js file in root

## Gulpfile.js

    'use strict';
    
    const  gulp  =  require('gulp');
    const  sass  =  require('gulp-sass')(require('sass'));
    const  sourcemaps  =  require('gulp-sourcemaps');
    // sass.compiler = require('sass')
    // const Fiber = require('fibers')
    // Fiber increases compile speed but throwing error now because of compatibility issue (watch for future version)
    
    // generate css Styles from SCSS
    function  buildStyles() {
	    return  gulp.src('./sass/**/*.scss')
		    .pipe(sourcemaps.init())
		    .pipe(sass().on('error', sass.logError))
		    .pipe(sourcemaps.write())
		    .pipe(gulp.dest('./css'));
    };
    
    exports.buildStyles  =  buildStyles;
    
    exports.default  =  function () {
	    gulp.watch('./sass/**/*.scss', buildStyles);
    };

   ## Commands
    gulp (run watch)
    gulp buildStyles (run build)

