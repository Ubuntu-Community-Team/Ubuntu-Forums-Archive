---
title: "Openoffice.org SDK seems broken in Edgy"
date: 2006-10-13
forum: Installation &amp; Upgrades
---

### Post by Nindi on 2006-10-13
I am not sure whether this is the correct place to post this, if not please let me know for future reference.
I want to be able to write addins for Ooo calc, for which I require the Openoffice.org SDK. This was not available in Dapper so I upgraded to Edgy yesterday. However it now seems to me that this package seems to be 'broken'.Specifical the utility 'regcomp' is missing. It should be in /usr/lib/openoffice/sdk/linux/bin .There are scripts there, regcomp, regcomp.bin and regcomp.bin.bin but the actual exectuable regcomp is missing, at least I think it is. I tried to build the RNG addin found at [http://wiki.services.openoffice.org/wiki/SimpleCalcAddIn](http://wiki.services.openoffice.org/wiki/SimpleCalcAddIn) under the 'Preparation' section. The error I get is 

 exec: 146: /usr/lib/openoffice/sdk/linux/bin/regcomp.bin.bin.bin: not found

when i execute the build script.

I hope someone can I put it right or tell me where I am going wrong.

I would like to add that the difficulty of extending spreadsheet functions in C++ on the Linux platform is a VERY significant flaw when compare to Windows. Addins for Excel are HUGLEY popular especialy in the financial industry and relied upon VERY heavily. Not having similar capabilites on Linux will always mean that its application in this industry will never be taken seriously.

---

