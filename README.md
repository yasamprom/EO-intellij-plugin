# eo-intellij-plugin

This is Intellij plugin for **[eo language](https://github.com/objectionary/eo)**. Plugin is implemented on Java and ANTLR4 grammar.

 **[ANTLR 4 adapter](https://github.com/antlr/antlr4-intellij-adaptor)** was used for generating lexer and parser classes.
First version contains syntax highlighting

## Usage
Installing is possible from IDEA. Type 'EO' in plugins search tab.

You may also install plugin from **[eo plugin page](https://plugins.jetbrains.com/plugin/19256-eo/versions)**
## Contributing
Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.
Please make sure to update tests as appropriate.

## Structure
In `src/main` you may find source code. Classes listed there are not autogenerated. They describe file type (EOFileType), parser (EOParserDefinition), highlighting colors etc.

You also need to generate other classes depends on grammar. They should be generated from .g4 file and moved into 
`java/org/eolang/jetbrains/parser`

Repository doesn't contain grammar file. File will be downloaded automatically before 'build' gradle task
Grammar file should appear in `main/antlr/org/antlr/jetbrains/eo/parser`.
Then you should generate needed classes from downloaded grammar file. 
You may use `generateGrammarSource` gradle task or do it manually (EO.g4 -> right click -> generate ANTLR recognizer)

Resources (icons and plugin.xml) are located in `src/resources`.


## Publishing
**Note that first publishing HAS TO be manually. Gradle task will work only for later releases.**

The easiest and most automatically way to publish plugin is using 2 gradle tasks 
1. **Building** (generates zip and puts it here `build/distributions`)
    
    Don't forget to change version in plugin.xml and gradle.properties!
    
    Run `buildPlugin`
   
    First time you should send zip archive to marketplace manually to **[JetBrains Marketplace](https://plugins.jetbrains.com)**
2. **Publishing**
    
    You will need to get private token here **[JetBrains Marketplace](https://plugins.jetbrains.com)** and pass its value into env. variable TOKEN 
    
    Then just run `publishPlugin` gradle task, zip archive will be pushed automatically.


## License
[MIT](https://choosealicense.com/licenses/mit/)