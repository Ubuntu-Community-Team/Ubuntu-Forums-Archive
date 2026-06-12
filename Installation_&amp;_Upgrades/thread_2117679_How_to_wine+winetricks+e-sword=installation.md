---
title: "How to: wine+winetricks+e-sword=installation"
date: 2013-02-19
forum: Installation &amp; Upgrades
---

### Post by Rogermana on 2013-02-19
How To install E-Sword on Ubuntu 12.04.
I have searched for weeks off and on to find a simple to follow walk-through on how to install E-Sword 10.1 with Wine1.5 onto Ubuntu 12.04.

I am appealing to someone to show me where such a walkthrough exists, or could someone write one based on the instruction I have found below. I have a fresh install of UbuntuCe 12.04, fully updated through terminal and synaptic, and the lastest Wine 1.5 and Winetricks. I have played with it and with the instructions and can't get it to do anything as it requires the learning of a computer script language and use of the wine interface, neither of which are intuitive, but promise to do a good job.

on winehq and biblesupport.com, they mention the following:

"this is what I do before installing e-sword. These instructions are for Kubuntu, but should work for other Ubuntu variations. 

Set oleaut32 to builtin in winecfg

In winetricks install

msls31
msxml3 *
vbrun6
vcrun6
wsh57

Once these are installed you can install E-sword and it should work.

* To install msxml3 winetricks will open an MS download site where you can get the file. Once downloaded put it in: home/user-name/.cache/winetricks/msxml3

To find the .cache type ctl-h while in your home dir to show the hidden files. You my have to reselect the files to have winetricks install them"

 I need really simple steps explained. I know how to open and use terminal, and open directory from the home folder, but I do not know many commands. what are the steps broken down? I believe there are hundreds of people like me wanting to use this program, but needing help.

Thankyou,
Roger

---

### Post by Rogermana on 2013-02-19
Example:
What does the first step mean:
Set oleaut32 to builtin in winecfg

How do you do that?
Roger

---

### Post by dino99 on 2013-02-19
its a plug & pray app  :lolflag:

its known to be badly supported against wine:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=25759&iTestingId=70800](http://appdb.winehq.org/objectManager.php?sClass=version&iId=25759&iTestingId=70800)

but why not simply instal bibletime, with use sword libraries ?

```
sudo apt-get install bibletime
```

):P

---

### Post by offgridguy on 2013-02-19
Are you using Ubuntu CE ? I believe bibletime is installed by default in UCE.

[http://distrowatch.com/?newsid=07438](http://distrowatch.com/?newsid=07438)

---

### Post by guyr34 on 2013-02-19
1. Install PlayOnLinux [http://www.playonlinux.com/en/download.html](http://www.playonlinux.com/en/download.html)
2. run PlayOnLinux. Tools / Run a local script : launch this script [ATTACH]231641[/ATTACH]

During the process don't install Mono and Gecko ...

---

### Post by grahammechanical on 2013-02-19
There are two sections of this forum that might interest you

Ubuntu Christian Edition

[http://ubuntuforums.org/forumdisplay.php?f=168]("http://ubuntuforums.org/forumdisplay.php?f=168")

Wine

[http://ubuntuforums.org/forumdisplay.php?f=313]("http://ubuntuforums.org/forumdisplay.php?f=313")

---

### Post by davidtrounce on 2013-02-20
> **guyr34 said:**
> 1. Install PlayOnLinux [http://www.playonlinux.com/en/download.html](http://www.playonlinux.com/en/download.html)
2. run PlayOnLinux. Tools / Run a local script : launch this script [ATTACH]231641[/ATTACH]

During the process don't install Mono and Gecko ...

Hi Guy,

I installed Playon Linux and it seems to run e-swordreally well - such a relief! However, I get this error on start up: "PlayOnLinux cannot find 7z (from P7ZIP full). 
You should install it to use PlayOnLinux"

I noticed also it installed Wine 1.5 during set up. I already had 1.4 installed. Should I (how can I) remove Wine 1.4? I have Synaptics but am unsure which (or even if) I should remove one of my Wine installations.

Thanks

David

---

### Post by peter1119 on 2013-04-21
> **Rogermana said:**
> I need really simple steps explained. I know how to open and use terminal, and open directory from the home folder, but I do not know many commands. what are the steps broken down? I believe there are hundreds of people like me wanting to use this program, but needing help.

Roger,
I was in the same boat you were in, not understanding what this set of instructions ment. I'm running Ubuntu 12.10, so I went to the Ubuntu Software Center and installed PlayOnLinux after I had installed Wine.

1. After I installed POL, I opened it up and clicked "Install", then "Install a non-listed program", and next.
2. I selected the option "Install a program in a new virtual drive", and made up a name, and clicked next, next.
3. It asked me for an install file, so I navigated to the downloads where I had put E-sword 10.10. From there it just put me through all the prompts of installation. I created a link on the desktop and tested it, but it still didn't have the search functions, so then I
4. Pushed "Configure" in PlayOnLinux, then on the "Install packages" tab, and found each of the packages and clicked Install: msls31, msxml3, vbrun6, vcrun6 and wsh57. 
5. Then in the "Wine" tab, I clicked "Configure Wine" and then the "Libraries" tab. In the dropdown for "New override for library" I found the thing called oleaut32, clicked it, and then clicked "Add". Then I clicked "Apply".
6. Opening the shortcut I created on my desktop brought up E-sword and the search worked!

I still don't know how to do all that directly in wine, but I hope this is a help to newer Ubuntu users like myself that really, really, really badly want to use E-Sword 10.10 in Ubuntu 12.10. 

For the faith of the gospel,
Peter

---

### Post by peter1119 on 2013-04-21
I forgot that I also installed 7zip from the Ubuntu Software Center after installing POL so that the popup message wouldn't come up again.

---

