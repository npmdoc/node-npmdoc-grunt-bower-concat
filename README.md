# api documentation for  [grunt-bower-concat (v1.0.0)](https://github.com/sapegin/grunt-bower-concat)  [![npm package](https://img.shields.io/npm/v/npmdoc-grunt-bower-concat.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-grunt-bower-concat) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-grunt-bower-concat.svg)](https://travis-ci.org/npmdoc/node-npmdoc-grunt-bower-concat)
#### Automatic concatenation of installed Bower components in right order.

[![NPM](https://nodei.co/npm/grunt-bower-concat.png?downloads=true)](https://www.npmjs.com/package/grunt-bower-concat)

[![apidoc](https://npmdoc.github.io/node-npmdoc-grunt-bower-concat/build/screenCapture.buildNpmdoc.browser._2Fhome_2Ftravis_2Fbuild_2Fnpmdoc_2Fnode-npmdoc-grunt-bower-concat_2Ftmp_2Fbuild_2Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-grunt-bower-concat/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-grunt-bower-concat/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-grunt-bower-concat/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "Artem Sapegin",
        "url": "http://sapegin.me/"
    },
    "bugs": {
        "url": "https://github.com/sapegin/grunt-bower-concat/issues"
    },
    "dependencies": {
        "async": "~1.5.2",
        "bower": "~1.7.7",
        "detective": "~4.3.1",
        "filesize": "~3.2.1",
        "lodash": "~4.3.0",
        "underscore.string": "~3.2.3"
    },
    "description": "Automatic concatenation of installed Bower components in right order.",
    "devDependencies": {
        "grunt": "~0.4.5",
        "grunt-cli": "~0.1.13",
        "grunt-contrib-clean": "~0.6.0",
        "grunt-contrib-jshint": "~0.11.2",
        "grunt-jscs": "~2.1.0",
        "grunt-mocha-test": "~0.12.7",
        "load-grunt-tasks": "~3.4.0",
        "mocha": "~2.4.5"
    },
    "directories": {},
    "dist": {
        "shasum": "f430c7b718704c6815215c6ca94d2fd5dd4a7b5b",
        "tarball": "https://registry.npmjs.org/grunt-bower-concat/-/grunt-bower-concat-1.0.0.tgz"
    },
    "engines": {
        "node": ">=0.10.0"
    },
    "gitHead": "56cd4fa7b0670335074c42cedf5d32fc393447ab",
    "homepage": "https://github.com/sapegin/grunt-bower-concat",
    "keywords": [
        "gruntplugin",
        "bower",
        "component",
        "package",
        "concat"
    ],
    "license": "MIT",
    "main": "tasks/bower-concat.js",
    "maintainers": [
        {
            "name": "sapegin",
            "email": "artem@sapegin.ru"
        }
    ],
    "name": "grunt-bower-concat",
    "optionalDependencies": {},
    "peerDependencies": {
        "grunt": ">=0.4.0"
    },
    "readme": "ERROR: No README data found!",
    "repository": {
        "type": "git",
        "url": "git://github.com/sapegin/grunt-bower-concat.git"
    },
    "scripts": {
        "pretest": "bower install",
        "test": "grunt"
    },
    "version": "1.0.0"
}
```



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module grunt-bower-concat](#apidoc.module.grunt-bower-concat)
1.  object <span class="apidocSignatureSpan">grunt-bower-concat.</span>configTools
1.  object <span class="apidocSignatureSpan">grunt-bower-concat.</span>dependencyTools

#### [module grunt-bower-concat.configTools](#apidoc.module.grunt-bower-concat.configTools)
1.  [function <span class="apidocSignatureSpan">grunt-bower-concat.configTools.</span>destinationConfigExists (data)](#apidoc.element.grunt-bower-concat.configTools.destinationConfigExists)
1.  [function <span class="apidocSignatureSpan">grunt-bower-concat.configTools.</span>extractDestData (data)](#apidoc.element.grunt-bower-concat.configTools.extractDestData)
1.  [function <span class="apidocSignatureSpan">grunt-bower-concat.configTools.</span>getValuesOfObject (object)](#apidoc.element.grunt-bower-concat.configTools.getValuesOfObject)

#### [module grunt-bower-concat.dependencyTools](#apidoc.module.grunt-bower-concat.dependencyTools)
1.  [function <span class="apidocSignatureSpan">grunt-bower-concat.dependencyTools.</span>buildDependencyGraph (module, dependencies, graph)](#apidoc.element.grunt-bower-concat.dependencyTools.buildDependencyGraph)
1.  [function <span class="apidocSignatureSpan">grunt-bower-concat.dependencyTools.</span>resolveDependencyGraph (module, resolved, unresolved, dependencies)](#apidoc.element.grunt-bower-concat.dependencyTools.resolveDependencyGraph)



# <a name="apidoc.module.grunt-bower-concat"></a>[module grunt-bower-concat](#apidoc.module.grunt-bower-concat)



# <a name="apidoc.module.grunt-bower-concat.configTools"></a>[module grunt-bower-concat.configTools](#apidoc.module.grunt-bower-concat.configTools)

#### <a name="apidoc.element.grunt-bower-concat.configTools.destinationConfigExists"></a>[function <span class="apidocSignatureSpan">grunt-bower-concat.configTools.</span>destinationConfigExists (data)](#apidoc.element.grunt-bower-concat.configTools.destinationConfigExists)
- description and source-code
```javascript
function destinationConfigExists(data) {
	if (data.dest) {
		return data.dest instanceof Object || typeof data.dest === 'string';
	}

	return false;
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.grunt-bower-concat.configTools.extractDestData"></a>[function <span class="apidocSignatureSpan">grunt-bower-concat.configTools.</span>extractDestData (data)](#apidoc.element.grunt-bower-concat.configTools.extractDestData)
- description and source-code
```javascript
function extractDestData(data) {

	if (destinationConfigExists(data)) {
		if (data.dest instanceof Object) {
			return extractMultiDestValues(data.dest);
		}
		else {
			return extractBackportDestination(data.dest);
		}
	}

	return [];
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.grunt-bower-concat.configTools.getValuesOfObject"></a>[function <span class="apidocSignatureSpan">grunt-bower-concat.configTools.</span>getValuesOfObject (object)](#apidoc.element.grunt-bower-concat.configTools.getValuesOfObject)
- description and source-code
```javascript
function getValues(object) {
	var values = [];
	Object.keys(object).forEach(function(key) {
		values.push(object[key]);
	});

	return values.reverse();
}
```
- example usage
```shell
n/a
```



# <a name="apidoc.module.grunt-bower-concat.dependencyTools"></a>[module grunt-bower-concat.dependencyTools](#apidoc.module.grunt-bower-concat.dependencyTools)

#### <a name="apidoc.element.grunt-bower-concat.dependencyTools.buildDependencyGraph"></a>[function <span class="apidocSignatureSpan">grunt-bower-concat.dependencyTools.</span>buildDependencyGraph (module, dependencies, graph)](#apidoc.element.grunt-bower-concat.dependencyTools.buildDependencyGraph)
- description and source-code
```javascript
function buildDependencyGraph(module, dependencies, graph) {
	if (module && !graph[module]) {
		graph[module] = [];
	}

	var dependencyNames = Object.keys(dependencies);
	dependencyNames.forEach(function(dependencyName) {
		var dependency = dependencies[dependencyName];

		if (module && graph[module].indexOf(dependencyName) === -1) {
			graph[module].push(dependencyName);
		}

		// Traverse down to this dependency dependencies:
		// Dependency-ception.
		if (dependency.dependencies) {
			buildDependencyGraph(dependencyName, dependency.dependencies, graph);
		}
	});
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.grunt-bower-concat.dependencyTools.resolveDependencyGraph"></a>[function <span class="apidocSignatureSpan">grunt-bower-concat.dependencyTools.</span>resolveDependencyGraph (module, resolved, unresolved, dependencies)](#apidoc.element.grunt-bower-concat.dependencyTools.resolveDependencyGraph)
- description and source-code
```javascript
function resolveDependencyGraph(module, resolved, unresolved, dependencies) {
	var moduleDependencies;
	if (module) {
		moduleDependencies = dependencies[module];
		if (!moduleDependencies) {
			throw new Error('Component ' + module + ' not installed. Try bower install --save ' + module);
		}
		unresolved.push(module);
	}
	else {
		moduleDependencies = Object.keys(dependencies);
	}

	moduleDependencies.forEach(function(moduleDependency) {
		if (resolved.indexOf(moduleDependency) === -1) {
			if (unresolved.indexOf(moduleDependency) !== -1) {
				throw new Error('Circular reference detected for ' + module + ' - ' + moduleDependency);
			}

			resolveDependencyGraph(moduleDependency, resolved, unresolved, dependencies);
		}
	});

	if (module) {
		resolved.push(module);
		unresolved = unresolved.splice(unresolved.indexOf(module), 1);
	}
}
```
- example usage
```shell
n/a
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
