---
title: "install help files for lazarus pascal IDE"
date: 2020-11-11
forum: Installation &amp; Upgrades
---

### Post by bjlockie on 2020-11-11
I installed the lazarus pascal IDE but it didn't install the help files.

Create a new application project.
It creates a new empty project.

Put the cursor in TForm:
```
type
  TForm1 = class(TForm)

```

Press F1.
It should open a help file but instead shows this error:

```
lcl.chm not found. Please put the chm help files in 
/usr/lib/lazarus/2.0.6/docs/chm;/usr/lib/lazarus/2.0.6/docs/html;/usr/lib/lazarus/2.0.6/docs/html/lcl
 or set the path to lcl.chm rtl.chm fcl.chm with "HelpFilesPath" in 
 Environment Options -> Help -> Help Options ->
 under HelpViewers - CHMHelpViewer
```

---

### Post by ActionParsnip on 2020-11-11
Does this help
[https://wiki.freepascal.org/Installing_Help_in_the_IDE](https://wiki.freepascal.org/Installing_Help_in_the_IDE)

---

### Post by bjlockie on 2020-11-13
Thanks.
I installed the chm files and it seems to work.

---

