---
title: "Ubuntu 10.04 (64bit) installed, but Win 7 disappeared?"
date: 2011-09-15
forum: Installation &amp; Upgrades
---

### Post by awinw on 2011-09-15
I had a HP laptop G61-420 computer with Microsfot Windows 7 home prem edition as sole OS. Today I decided to add Ubuntu as dual OS.

I partitioned a new 90GB (from 304GB) to install Ubuntu 10.04 (64bit),  Ubuntu installation succeeded, but Win 7 disappeared!

I tried to restore Win 7 with its Recovery Manager, but
it failed. 

As  I bought this HP Win 7 laptop second-hand,the previous owner did not give me a DVD disk of OS. He said I could easily restore it with built-in Recovery Manager. 

Please help how can I re-instate this Win 7 withOUT recovery manager NOR DVD disk??

---

### Post by oldfred on 2011-09-15
First lets see what is where.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by awinw on 2011-09-16
> **oldfred said:**
> First lets see what is where.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
......o get .sh to run.

Sorry, I do not know  where/how to download:
in the following page, the link connects to nowhere except for  its functions:  thanks for more help!

[LIST]
[*]Boot into any Linux based operating system, LiveCD or LiveUSB with an Internet connection.
[*][Download the Boot Info Script]("http://sourceforge.net/projects/bootinfoscript")
[*]Extract the zip file to a directory of your choice.
[*]Open a terminal....
[/LIST]

---

### Post by oldfred on 2011-09-16
Try green button on the page, it should then download.

---

### Post by awinw on 2011-09-16
> **oldfred said:**
> Try green button on the page, it should then download.

Yes, but what was already downloaded is an .exe file,,
there is a warning like this:

 Archive:  /tmp/Babylon9_setup-1.exe
[/tmp/Babylon9_setup-1.exe]
  End-of-central-directory signature not found.  Either this file is not  a zipfile, or it constitutes one disk of a multi-part archive.  
zipinfo:  cannot find zipfile directory in one of /tmp/Babylon9_setup-1.exe or           /tmp/Babylon9_setup-1.exe.zip, and cannot find /tmp/Babylon9_setup-1.exe.ZIP, period.

---

### Post by Hakunka-Matata on 2011-09-16
As you say, that's the wrong file.  It is a .zip file now.  Try the link in my signature for boot_info_script.sh

Here's what I see when going to the boot_info_script link in my signature

---

### Post by oldfred on 2011-09-16
Where are you getting an .exe file from? Linux does not even use exe except  with .wine.

Are you trying to download in another Windows computer and have a virus? You should use Ubuntu install or liveCD.

---

### Post by awinw on 2011-09-17
> **oldfred said:**
> Try green button on the page, it should then download.

yes, I got it and unzipped it.
this long text is too much for me to understand now.
not sure which part should I paste here.

---

### Post by srs5694 on 2011-09-17
Run the script. It will create a file called RESULTS.txt. Post the *entire* RESULTS.txt file, either as an attachment or between [noparse]```
[/noparse] and [noparse]
```[/noparse] tags.

---

