
﻿Introduction
============

PSScriptAnalyzer is a static code checker for Windows PowerShell modules and scripts. PSScriptAnalyzer checks the quality of Windows PowerShell code by running a set of rules. The rules are based on PowerShell best practices identified by PowerShell Team and the community. It generates DiagnosticResults (errors and warnings) to inform users about potential code defects and suggests possible solutions for improvements.

PSScriptAnalyzer is shipped with a collection of built-in rules that checks various aspects of PowerShell code such as presence of uninitialized variables, usage of PSCredential Type, usage of Invoke-Expression etc. Additional functionalities such as exclude/include specific rules are also supported.

PSScriptAnalyzer cmdlets
======================
```
Get-ScriptAnalyzerRule [-CustomizedRulePath <string[]>] [-Name <string[]>] [<CommonParameters>] [-Severity <string[]>]

Invoke-ScriptAnalyzer [-Path] <string> [-CustomizedRulePath <string[]>] [-ExcludeRule <string[]>] [-IncludeRule <string[]>] [-Severity <string[]>] [-Recurse] [<CommonParameters>]
```

Requirements
============

WS2012R2 / Windows 8.1 / Windows OS running **PowerShell v5.0** and **Windows Management Framework 5.0 Preview**

Download the latest WMF package from [Windows Management Framework 5.0 Preview](http://go.microsoft.com/fwlink/?LinkId=398175).

Installation
============

1. Build the Code using Visual Studio [solution part of the repo] and navigate to the binplace location [``~/ProjectRoot/PSScriptAnalyzer``]

2. In PowerShell Console:
```powershell
Import-Module PSScriptAnalyzer
```
If you have previous version of PSScriptAnalyzer installed on your machine, you may need to override old binaries by copying content of [``~/ProjectRoot/PSScriptAnalyzer``] to PSModulePath. 

To confirm installation: run ```Get-ScriptAnalyzerRule``` in the PowerShell console to obtain the built-in rules

Building the Code
=================

Use Visual Studio to build "ScriptAnalyzer.sln". Use ~/PSScriptAnalyzer/ folder to load PSScriptAnalyzer.psd1

**Note: If there are any build errors, please refer to Requirements section and make sure all dependencies are properly installed**

Running Tests
=============

Pester-based ScriptAnalyzer Tests are located in ```<branch>/PSScriptAnalyzer/Tests``` folder

* Ensure Pester is installed on the machine
* Go the Tests folder in your local repository
* Run Engine Tests:
.\InvokeScriptAnalyzer.tests.ps1
* Run Tests for Built-in rules:
.\*.ps1 (Example - .\ AvoidConvertToSecureStringWithPlainText.ps1)
*You can also run all tests under \Engine or \Rules by calling Invoke-Pester in the Engine/Rules directory.
 
Project Management Dashboard
==============================

You can track issues, pull requests, backlog items here:

[![Stories in progress](https://badge.waffle.io/PowerShell/PSScriptAnalyzer.png?label=In%20Progress&title=In%20Progress)](https://waffle.io/PowerShell/PSScriptAnalyzer)

[![Stories in ready](https://badge.waffle.io/PowerShell/PSScriptAnalyzer.png?label=ready&title=Ready)](https://waffle.io/PowerShell/PSScriptAnalyzer)

[![Stories in backlog](https://badge.waffle.io/PowerShell/PSScriptAnalyzer.png?label=BackLog&title=BackLog)](https://waffle.io/PowerShell/PSScriptAnalyzer)


Contributing to ScriptAnalyzer
==============================

You are welcome to contribute to this project. There are many ways to contribute:

1. Submit a bug report via [Issues]( https://github.com/PowerShell/PSScriptAnalyzer/issues). For a guide to submitting good bug reports, please read [Painless Bug Tracking](http://www.joelonsoftware.com/articles/fog0000000029.html).
2. Verify fixes for bugs.
3. Submit your fixes for a bug. Before submitting, please make sure you have:
  * Performed code reviews of your own
  * Updated the test cases if needed
  * Run the test cases to ensure no feature breaks or test breaks
  * Added the test cases for new code
4. Submit a feature request.
5. Help answer questions in the discussions list.
6. Submit test cases.
7. Tell others about the project.
8. Tell the developers how much you appreciate the product!

You might also read these two blog posts about contributing code: [Open Source Contribution Etiquette](http://tirania.org/blog/archive/2010/Dec-31.html) by Miguel de Icaza, and [Don’t “Push” Your Pull Requests](http://www.igvita.com/2011/12/19/dont-push-your-pull-requests/) by Ilya Grigorik.

Before submitting a feature or substantial code contribution, please discuss it with the Windows PowerShell team via [Issues](https://github.com/PowerShell/PSScriptAnalyzer/issues), and ensure it follows the product roadmap. Note that all code submissions will be rigorously reviewed by the Windows PowerShell Team. Only those that meet a high bar for both quality and roadmap fit will be merged into the source.
