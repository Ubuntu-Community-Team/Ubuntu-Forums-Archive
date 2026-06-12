---
title: "Upgrade / application install / removal problem"
date: 2011-01-30
forum: Installation &amp; Upgrades
---

### Post by Norwegian-Blue on 2011-01-30
There seems to be a problem with my Brother HL-2030 printer driver.

I am now unable to update Ubuntu via the undate manager. I get the following error:


 "It is impossible to install or remove any software. Please use the  package manager "Synaptic" or run "sudo apt-get install -f" in a  terminal to fix this issue at first."
 

When I run the command I get:
 

 The package brhl2030lpr needs to be reinstalled, but I can't find an archive for it.
 

But it does not tell me where it is looking !!!
 

Now I think I know where the package is, if someone can tell me where it should be placed maybe this will fix my problem.


 I am not able to install or remove any software via the Ubuntu  Software Centre. Trying to manually uninstall the brhl2030lpr package  from the command line and I get:
 

"dpkg: error processing brhl2030lpr (--purge):
 Package is in a very bad inconsistent state - you should reinstall it before attempting a removal.
Errors were encountered while processing:  brhl2030lpr"
 

But re-installing it did not help.
 

Can anyone help me, or point, me to another place were I may be able to get help.
 

Thanks
Ian

---

### Post by thewho1050 on 2011-01-30
you should delete the file using

```
rm (filename)
```

if you dont know where it is use

```
locate (filename)
```

then reinstall the package from scratch using ubuntu software.

---

### Post by kansasnoob on 2011-01-30
You might open Synaptic, click on Custom filters, then select Broken. Does it happen to show up there?

If so highlight it, right-click, select Properties, then click on the Installed files tab. Then make a note of all installed files and very, very careful remove them.

Then try:

```
sudo apt-get clean
```

```
sudo dpkg --configure -a
```

And from there continue to try and update, install packages, etc.

---

### Post by Norwegian-Blue on 2011-01-30
> **thewho1050 said:**
> you should delete the file using

```
rm (filename)
```if you dont know where it is use

```
locate (filename)
```then reinstall the package from scratch using ubuntu software.

Sorry, but which (filename) are you referring to. My problem is that I do not know which (filename) Ubuntu is trying to find.

---

### Post by Norwegian-Blue on 2011-01-30
> **kansasnoob said:**
> You might open Synaptic, click on Custom filters, then select Broken. Does it happen to show up there?

If so highlight it, right-click, select Properties, then click on the Installed files tab. Then make a note of all installed files and very, very careful remove them.

Then try:

```
sudo apt-get clean
``````
sudo dpkg --configure -a
```And from there continue to try and update, install packages, etc.

When I try and open Synaptic, I get the follwing message:

E: The package brhl2030lpr needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

Regards
Ian

---

### Post by Cheesehead on 2011-01-30
Remember back to when you installed the printer driver originally? You probably downloaded it and followed some instructions.

Since *you* downloaded it, the system doesn't know where you got it from. The error message is the system telling you that it doesn't know where to get it from.

One solution:
1) Delete (remove) the printer driver from your system.
2) Upgrade
3) Reinstall the printer driver. Did you keep the original driver download? If not, go back to the website and download it again.

---

### Post by Norwegian-Blue on 2011-01-30
> **Cheesehead said:**
> Remember back to when you installed the printer driver originally? You probably downloaded it and followed some instructions.

Since *you* downloaded it, the system doesn't know where you got it from. The error message is the system telling you that it doesn't know where to get it from.

One solution:
1) Delete (remove) the printer driver from your system.
2) Upgrade
3) Reinstall the printer driver. Did you keep the original driver download? If not, go back to the website and download it again.


Which file do I need to delete ?

The install involved two .deb packages and an install script.
I have opened both packages and deleted all the files files on my system that appear to have been copied from these packages. 

But I still get the same problem when I open Synaptic.

I have tried to read the install script, but it is mostly gibberish to me.

What is Synaptic reading to determine that there is a problem ?

Regards
Ian

---

### Post by Norwegian-Blue on 2011-01-30
I tried the "Update Manager" and it seems that after I deleted the files, the Update Manager was able to force the removal of the package. 

Now the problem has gone away :)

Thanks for the help.

---

