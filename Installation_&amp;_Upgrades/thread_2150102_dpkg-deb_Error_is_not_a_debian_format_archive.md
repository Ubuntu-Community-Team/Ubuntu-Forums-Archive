---
title: "dpkg-deb Error is not a debian format archive"
date: 2013-05-30
forum: Installation &amp; Upgrades
---

### Post by seruling on 2013-05-30
I download some package from several web that claim that the software tested under Ubuntu.
When I download them, and run dpkg, i receive message like this:
```
[COLOR=#000080]dpkg-deb: error: `AdbeRdr9.5.5-1_i486linux_enu.bin' is not a debian format archive[/COLOR]
[COLOR=#000080]dpkg: error processing AdbeRdr9.5.5-1_i486linux_enu.bin (--install):[/COLOR]
[COLOR=#000080] subprocess dpkg-deb --control returned error exit status 2[/COLOR]
[COLOR=#000080]Errors were encountered while processing:[/COLOR]
[COLOR=#000080] AdbeRdr9.5.5-1_i486linux_enu.bin[/COLOR]
```
That was one of them. Form several package I try to install manually from terminal, only google chrome succeed (uses "dpkg -f ..." ).

---

### Post by fantab on 2013-05-31
This is the reason why, as far as it is possible, you MUST use [Ubuntu 'Repositories']("https://help.ubuntu.com/community/Repositories/Ubuntu") to download software. Almost everything you need is available through Ubuntu 'Repositories'. Do do this simply use 'Software Center'.
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

To be able to download and install certain software, like Adobe/Acrobat Reader you must enable 'Canonical PARTNERS' and 'INDEPENDENT' Repositories. To do this open 'Software Center' -> Edit -> software sources -> other software -> **select** Canonical Partners and Independent.

After making the changes, from Terminal [Ctrl+Alt+T] run:
sudo apt-get update

---

### Post by sanderj on 2013-05-31
> **seruling said:**
> I download some package from several web that claim that the software tested under Ubuntu.
When I download them, and run dpkg, i receive message like this:
```
[COLOR=#000080]dpkg-deb: error: `AdbeRdr9.5.5-1_i486linux_enu.bin' is not a debian format archive[/COLOR]
[COLOR=#000080]dpkg: error processing AdbeRdr9.5.5-1_i486linux_enu.bin (--install):[/COLOR]
[COLOR=#000080] subprocess dpkg-deb --control returned error exit status 2[/COLOR]
[COLOR=#000080]Errors were encountered while processing:[/COLOR]
[COLOR=#000080] AdbeRdr9.5.5-1_i486linux_enu.bin[/COLOR]
```
That was one of them. Form several package I try to install manually from terminal, only google chrome succeed (uses "dpkg -f ..." ).

dpkg-deb is for installing .deb files (not .bin files).

And like the other poster said: install Adobe Reader via the Ubuntu Software Center.

---

### Post by seruling on 2013-05-31
Thank you for replying.

But I still confuse about installing 3rd party software.
Currently, the company where I work using an accounting software that work under Windows.
My company plans to migrate to Ubuntu. Some divisions already migrated, except accounting division.
We already have a lot of data already with that software (under windows).
They provide linux version of that accounting software. I still try to install that accounting software under Ubuntu with no luck. 
here is the link: [http://deluxeaccounting.com/index.php?option=com_wrapper&view=wrapper&Itemid=57](http://deluxeaccounting.com/index.php?option=com_wrapper&view=wrapper&Itemid=57)

---

### Post by sanderj on 2013-05-31
We could help you installing the software from [http://deluxeaccounting.com/index.php?option=com_wrapper&view=wrapper&Itemid=57](http://deluxeaccounting.com/index.php?option=com_wrapper&view=wrapper&Itemid=57) , but first a few questions:

Shouldn't the IT department take care of installing that software? Based on your post, I have the idea you're not the IT guy.
If that accounting software needs to be installed, why are you trying to install Adobe Reader?

---

### Post by seruling on 2013-05-31
About adobe reader thing,
I often receive pdf files from email. A lot of them are scaned document and converted to pdf.
The problem is when I need view a landscape paper, current ubuntu pdf viewer can't rotate the view. That's why i want to install adobe pdf reader

---

### Post by sanderj on 2013-05-31
Ah. So: you want to install Adobe Reader. Did you follow the advice from @fantab? Then search for "acroread" and install it

Or, if you like command line more:


```
sudo add-apt-repository "deb http://archive.canonical.com/ precise partner"
sudo apt-get update
sudo apt-get install acroread
```

---

### Post by sanderj on 2013-06-01
So ... that worked for you?

---

### Post by seruling on 2013-06-01
Thank you,
I did the [COLOR=#000000][FONT=Ubuntu Mono]sudo add-apt-repository "deb [http://archive.canonical.com/](http://archive.canonical.com/) precise partner" and now can install acrobat reader.
Rotate view works fine.

[/FONT][/COLOR]

---

