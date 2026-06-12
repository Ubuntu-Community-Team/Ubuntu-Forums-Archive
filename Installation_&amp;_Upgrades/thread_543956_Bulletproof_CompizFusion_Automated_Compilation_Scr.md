---
title: "Bulletproof CompizFusion Automated Compilation Script - git/stable"
date: 2007-09-05
forum: Installation &amp; Upgrades
---

### Post by phaedOne on 2007-09-05
[COLOR="Navy"]
[SIZE="2"]**This script aims to be an all inclusive tool that will allow you to install/update Compiz-Fusion, Emerald, and Fusion-Icon from git or stable source entirely or by parts in Ubuntu Feisty/Gutsy**[/SIZE][/COLOR]

[COLOR="DarkOrange"]Feel free to post patches or improvements for the script, I will update it as I get them.[/color]

[Bulletproof CF Automated Compilation Script  v1]("http://photos.dcstealthy.com/phaedrus/bp-compiz")

To install the script, right-click the link above and choose "Save Link As...", give it name "bp-compiz" and save it to the Desktop.  

Open the terminal then run the following command to make the file execuatable:
```

sudo chmod 755 ~/Desktop/bp-compiz

```

Then run it with:

```

cd ~/Desktop
sudo bash bp-compiz

```


[SIZE="3"]**Overview:**[/SIZE]


**The main menu:**

```

 0. Install...
 1. Update
 2. Uninstall
 3. README

```

[list]**Install** will take you to the install menu[/list]
[list]**Update** will re-download and re-compile installed components[/list]
[list]**Uninstall **will remove all previously installed components by this script[/list]


**The Install menu:**

You can choose to do an unassisted install of all the components or install them individually:

```

**  0. Full Installation (1-16)**
  1. Uninstall all previous versions (compiz/beryl/emerald)
  2. Download/Install Required Dependencies (git-core automake ...)
  3. Download/Install Compiz' Dependencies
  4. Download/Install libX11 with xcb support (required for git)
  5. Download/Install Compiz Fusion
  6. Download/Install Option Code Generator
  7. Download/Install Settings Library for Plugins
  8. Download/Install CompizConfig-Python
  9. Download/Install Settings Manager
 10. Download/Install Main Plugins
 11. Download/Install Extra Plugins
 12. Download/Install Unsupported Plugins
 13. Download/Install Emerald
 14. Download/Install Emerald Themes
 15. Download/Install Fusion-Icon
 16. Add argb-glx-visuals to xorg.conf

```

[list]Option 1 removes emerald*, compiz*, beryl*, desktop-effects using apt-get remove.  It also uninstalls any everything previously installed with this script[/list]
[list]Option 4 is automatically  skipped  if you are installing from stable source[/list]
[list]Option 16 is automatically skipped if you don't have the nvidia device in your xorg.conf[/list]

**The report: **

At the end of the installation the script will output a report for troubleshooting purposes with the exit status of each component's install process.  It looks something like this:

```

 * Installed Required Dependencies                              **[COLOR="SeaGreen"][OK][/COLOR]**
 * Installed Compiz' Dependencies                               **[COLOR="SeaGreen"][OK][/COLOR]**
 * Installed Compiz Fusion                                      **[COLOR="SeaGreen"][OK][/COLOR]**
 * Installed Option Code Generator                              **[COLOR="SeaGreen"][OK][/COLOR]**
 * Installed Settings Library for Plugins                       **[COLOR="SeaGreen"][OK][/COLOR]**
 * Installed CompizConfig-Python                                **[COLOR="SeaGreen"][OK][/COLOR]**
 * Installed Settings Manager                                   **[COLOR="SeaGreen"][OK][/COLOR]**
 * Installed Main Plugins                                       **[COLOR="SeaGreen"][OK][/COLOR]**
 * Installed Extra Plugins                                      **[COLOR="SeaGreen"][OK][/COLOR]**
 * Installed Unsupported Plugins                                **[COLOR="SeaGreen"][OK][/COLOR]**
 * Installed Emerald                                            **[COLOR="SeaGreen"][OK][/COLOR]**
 * Installed Emerald Themes                                     **[COLOR="SeaGreen"][OK][/COLOR]**
 * Installed Fusion-Icon                                 ** [COLOR="Red"] [Error 2][/COLOR]**
 * Added argb-glx-visuals to xorg.conf                          **[COLOR="SeaGreen"][OK][/COLOR]**

```

To set compiz-fusion to run at startup add fusion-icon to your Sessions (Menu->System->Preferences->Sessions) and reboot.
After the reboot right click on the fusion-icon on your systray and do (Select Window Manager->Compiz)

[COLOR="DarkOrange"]This is a refactored and enhanced version of  ElmonGW's CF Installer script:
[http://ubuntuforums.org/showthread.php?t=508769](http://ubuntuforums.org/showthread.php?t=508769)[/COLOR]

---

### Post by Nigmah on 2007-09-05
when i click to download it just opens up another window with the code inside. Might wanna fix that. 
I'm running off of windows right now but i'll check if righe clicking it and saving it as .sh works.

---

### Post by Zer0Nin3r on 2007-09-05
> **Nigmah said:**
> when i click to download it just opens up another window with the code inside. Might wanna fix that. 
I'm running off of windows right now but i'll check if righe clicking it and saving it as .sh works.

Try right click 'Save-As'.  Then save the script with a file name of your choice followed by the extension

---

### Post by ortwein on 2007-09-05
I'm really new at this.

Once I click "save as" on the link above, and it brings up the dialog box, what name should I give the file...and where should I save it?

ALSO....I've been downloading it to my desktop and double clicking it which brings up KATE.  This isn't right is it?

help needed...

confused...

Mark

---

### Post by phaedOne on 2007-09-06
> **ortwein said:**
> I'm really new at this.

Once I click "save as" on the link above, and it brings up the dialog box, what name should I give the file...and where should I save it?

ALSO....I've been downloading it to my desktop and double clicking it which brings up KATE.  This isn't right is it?

help needed...

confused...

Mark

I edited the post with better instructions.

---

### Post by airtonix on 2007-09-06
No version for feisty?

---

### Post by ortwein on 2007-09-06
Wow Phaed...awesome job!

---

### Post by mythik on 2007-09-07
what would I need to change to get it to work on feisty?

---

### Post by st33med on 2007-09-09
This looks like a really good script. Still installing...

---

### Post by st33med on 2007-09-09
An error that I don't think affects me, but:
```
dpkg-gencontrol: warning: unknown substitution variable ${misc:Depends}
dpkg-gencontrol: warning: unknown substitution variable ${shlibs:Depends}
dpkg-gencontrol: warning: unknown substitution variable ${misc:Depends}
dpkg-gencontrol: warning: unknown substitution variable ${shlibs:Depends}
dpkg-gencontrol: warning: unknown substitution variable ${misc:Depends}
dpkg-gencontrol: warning: unknown substitution variable ${misc:Depends}
dpkg-gencontrol: warning: unknown substitution variable ${shlibs:Depends}
dpkg-gencontrol: warning: unknown substitution variable ${misc:Depends}
dpkg-gencontrol: warning: unknown substitution variable ${shlibs:Depends}
dpkg-gencontrol: warning: unknown substitution variable ${misc:Depends}

``` 
The script looks more solid. Guess that's why it is called 'bulletproof' ;)

---

### Post by st33med on 2007-09-09
Very
very
very
nice.:)

---

### Post by bobbob1016 on 2007-09-15
Great script.

Some minor improvements that I could think of:

You could add a "Stability Check", that notifies the user if there is a known stability issue.  The stability is available here [http://status.compiz-fusion.org/](http://status.compiz-fusion.org/)  as in "There are no known stability issues with this git version."  or "There are some issues with stability."  or something like that.

See about checking for envy being installed, and ask the user if they would like drivers installed, for nvidia cards.  More of a unified approach.

The script also does some compiling or something, even if I already have the newest git version.  Not sure if it is supposed to or not.

You could also add a 4th option to the main menu, an "Exit" option.  Not sure if it is bad to just close the window, but just a thought.

---

### Post by WACD on 2007-09-16
I installed...and everything is very nice and fine...
but then if i turn on CompizFusion...
no matter what I do...my top is missing...
the top of every window...the place that i can max. min. or close...
and they are all stuck and can't move...

everything works fine else then this...
my computer is running on 7600GT...
it is dual screen but with very diff resolutions...
will that be a problem...?

---

### Post by lupomarano on 2007-09-16
Can I use this script on a Debian box?

---

### Post by phaedOne on 2007-09-18
> **WACD said:**
> I installed...and everything is very nice and fine...
but then if i turn on CompizFusion...
no matter what I do...my top is missing...
the top of every window...the place that i can max. min. or close...
and they are all stuck and can't move...

everything works fine else then this...
my computer is running on 7600GT...
it is dual screen but with very diff resolutions...
will that be a problem...?

This means you have the window manager not loaded.  Try:

```

emerald --replace&

```

---

### Post by christian88 on 2007-09-18
sorry, i found a problem during this installation...i use your script but suddenly i receved this error:

```
compiz.c:42:25: error: compiz-core.h: No such file or directory
compiz.c: In function 'initColorValue':
compiz.c:515: warning: implicit declaration of function 'MAX'
compiz.c:515: warning: nested extern declaration of 'MAX'
compiz.c:515: warning: implicit declaration of function 'MIN'
compiz.c:515: warning: nested extern declaration of 'MIN'
compiz.c: In function 'initIntInfo':
compiz.c:720: error: 'MINSHORT' undeclared (first use in this function)
compiz.c:720: error: (Each undeclared identifier is reported only once
compiz.c:720: error: for each function it appears in.)
compiz.c:721: error: 'MAXSHORT' undeclared (first use in this function)
compiz.c: In function 'initFloatInfo':
compiz.c:788: error: 'MINSHORT' undeclared (first use in this function)
compiz.c:789: error: 'MAXSHORT' undeclared (first use in this function)
make[2]: *** [compiz.lo] Error 1
make[2]: Leaving directory `/home/chris/.compiz-setup/libcompizconfig/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/chris/.compiz-setup/libcompizconfig'
make: *** [all] Error 2
[Failed] The previous process exited with error 2
chris@chris-desktop:~/Desktop$ 

```

can you help me please?

---

### Post by phaedOne on 2007-10-07
> **christian88 said:**
> sorry, i found a problem during this installation...i use your script but suddenly i receved this error:

```
compiz.c:42:25: error: compiz-core.h: No such file or directory
compiz.c: In function 'initColorValue':
compiz.c:515: warning: implicit declaration of function 'MAX'
compiz.c:515: warning: nested extern declaration of 'MAX'
compiz.c:515: warning: implicit declaration of function 'MIN'
compiz.c:515: warning: nested extern declaration of 'MIN'
compiz.c: In function 'initIntInfo':
compiz.c:720: error: 'MINSHORT' undeclared (first use in this function)
compiz.c:720: error: (Each undeclared identifier is reported only once
compiz.c:720: error: for each function it appears in.)
compiz.c:721: error: 'MAXSHORT' undeclared (first use in this function)
compiz.c: In function 'initFloatInfo':
compiz.c:788: error: 'MINSHORT' undeclared (first use in this function)
compiz.c:789: error: 'MAXSHORT' undeclared (first use in this function)
make[2]: *** [compiz.lo] Error 1
make[2]: Leaving directory `/home/chris/.compiz-setup/libcompizconfig/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/chris/.compiz-setup/libcompizconfig'
make: *** [all] Error 2
[Failed] The previous process exited with error 2
chris@chris-desktop:~/Desktop$ 

```

can you help me please?

fixed a few bugs in the script including yours.  redownload the script and all should run smoothly.

---

### Post by celticbhoy on 2007-10-07
I'm getting the error as christian88, and as the post was there before I tried the script, I'm guessing the problem aint sorted. I have been trying the full install, if I go bit-by-bit will it help to sort this ???

---

### Post by bobo on 2007-10-07
Thank you very much for the awesome script.  Unfortunately I'm also getting the  MINSHORT and MAXSHORT error that phaedOne is getting.  I downloaded the script on the 8th of October.  Was I to early in getting the updated script?

bobo

---

### Post by shockwaver on 2007-10-11
I hate to be reposting the same errors that other people are having, however I'm getting something that isn't shown in the log above:
Edit: It appears this is the "Settings Library for Plugins" script/section.
```
compiz.c: In function 'initColorValue':
compiz.c:512: warning: implicit declaration of function 'MAX'
compiz.c:512: warning: nested extern declaration of 'MAX'
compiz.c:512: warning: implicit declaration of function 'MIN'
compiz.c:512: warning: nested extern declaration of 'MIN'
compiz.c: At top level:
compiz.c:565: error: 'ShiftMask' undeclared here (not in a function)
compiz.c:566: error: 'ControlMask' undeclared here (not in a function)
compiz.c:567: error: 'Mod1Mask' undeclared here (not in a function)
compiz.c:568: error: 'Mod2Mask' undeclared here (not in a function)
compiz.c:569: error: 'Mod3Mask' undeclared here (not in a function)
compiz.c:570: error: 'Mod4Mask' undeclared here (not in a function)
compiz.c:571: error: 'Mod5Mask' undeclared here (not in a function)
compiz.c:572: error: 'CompAltMask' undeclared here (not in a function)
compiz.c:573: error: 'CompMetaMask' undeclared here (not in a function)
compiz.c:574: error: 'CompSuperMask' undeclared here (not in a function)
compiz.c:575: error: 'CompHyperMask' undeclared here (not in a function)
compiz.c:576: error: 'CompModeSwitchMask' undeclared here (not in a function)
compiz.c: In function 'stringToKey':
compiz.c:612: warning: implicit declaration of function 'XStringToKeysym'
compiz.c:612: warning: nested extern declaration of 'XStringToKeysym'
compiz.c:617: error: 'NoSymbol' undeclared (first use in this function)
compiz.c:617: error: (Each undeclared identifier is reported only once
compiz.c:617: error: for each function it appears in.)
compiz.c:617: warning: assignment makes integer from pointer without a cast
compiz.c: In function 'initIntInfo':
compiz.c:784: error: 'MINSHORT' undeclared (first use in this function)
compiz.c:784: warning: assignment makes integer from pointer without a cast
compiz.c:785: error: 'MAXSHORT' undeclared (first use in this function)
compiz.c:785: warning: assignment makes integer from pointer without a cast
compiz.c: In function 'initFloatInfo':
compiz.c:852: error: 'MINSHORT' undeclared (first use in this function)
compiz.c:852: error: incompatible types in assignment
compiz.c:852: warning: statement with no effect
compiz.c:853: error: 'MAXSHORT' undeclared (first use in this function)
compiz.c:853: error: incompatible types in assignment
compiz.c:853: warning: statement with no effect
make[2]: *** [compiz.lo] Error 1
make[2]: Leaving directory `/home/chris/.compiz-setup/libcompizconfig/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/chris/.compiz-setup/libcompizconfig'
make: *** [all] Error 2
[Failed] The previous process exited with error 2
```

Any help?

---

### Post by celticbhoy on 2007-10-11
Just to update I got the script to work by NOT choosing the stable version when it was running.

---

### Post by CypherDelic on 2007-10-22
I have to re-announce this bug. I recently downloaded bp.compiz-script, and tried by installing  git-unstable with build-dependencies OR default-dependencies. I'm with Gutsy Final, kernel 2.6.22-14. This is what I receive:

> 
compiz.c: In function 'initColorValue':
compiz.c:512: warning: implicit declaration of function 'MAX'
compiz.c:512: warning: nested extern declaration of 'MAX'
compiz.c:512: warning: implicit declaration of function 'MIN'
compiz.c:512: warning: nested extern declaration of 'MIN'
compiz.c: At top level:
compiz.c:565: error: 'ShiftMask' undeclared here (not in a function)
compiz.c:566: error: 'ControlMask' undeclared here (not in a function)
compiz.c:567: error: 'Mod1Mask' undeclared here (not in a function)
compiz.c:568: error: 'Mod2Mask' undeclared here (not in a function)
compiz.c:569: error: 'Mod3Mask' undeclared here (not in a function)
compiz.c:570: error: 'Mod4Mask' undeclared here (not in a function)
compiz.c:571: error: 'Mod5Mask' undeclared here (not in a function)
compiz.c:572: error: 'CompAltMask' undeclared here (not in a function)
compiz.c:573: error: 'CompMetaMask' undeclared here (not in a function)
compiz.c:574: error: 'CompSuperMask' undeclared here (not in a function)
compiz.c:575: error: 'CompHyperMask' undeclared here (not in a function)
compiz.c:576: error: 'CompModeSwitchMask' undeclared here (not in a function)
compiz.c: In function 'stringToKey':
compiz.c:612: warning: implicit declaration of function 'XStringToKeysym'
compiz.c:612: warning: nested extern declaration of 'XStringToKeysym'
compiz.c:617: error: 'NoSymbol' undeclared (first use in this function)
compiz.c:617: error: (Each undeclared identifier is reported only once
compiz.c:617: error: for each function it appears in.)
compiz.c:617: warning: assignment makes integer from pointer without a cast
compiz.c: In function 'initIntInfo':
compiz.c:784: error: 'MINSHORT' undeclared (first use in this function)
compiz.c:784: warning: assignment makes integer from pointer without a cast
compiz.c:785: error: 'MAXSHORT' undeclared (first use in this function)
compiz.c:785: warning: assignment makes integer from pointer without a cast
compiz.c: In function 'initFloatInfo':
compiz.c:852: error: 'MINSHORT' undeclared (first use in this function)
compiz.c:852: error: incompatible types in assignment
compiz.c:852: warning: statement with no effect
compiz.c:853: error: 'MAXSHORT' undeclared (first use in this function)
compiz.c:853: error: incompatible types in assignment
compiz.c:853: warning: statement with no effect
make[2]: *** [compiz.lo] Fehler 1
make[2]: Verlasse Verzeichnis '/home/cypher/.compiz-setup/libcompizconfig/src'
make[1]: *** [all-recursive] Fehler 1
make[1]: Verlasse Verzeichnis '/home/cypher/.compiz-setup/libcompizconfig'
make: *** [all] Fehler 2
[Failed] The previous process exited with error 2
cypher@HaeckFlaisch:~$

This is the hole pastebin of compiling compizconfig: pastebin.com/m42ca620a

I get this additional Information:

> Note: moving to "0.6.0" which isn't a local branch
If you want to create a new branch from this checkout, you may do so
(now or later) by using -b with the checkout command again. Example:
  git checkout -b <new_branch_name>
HEAD is now at 5615cac... bump version to 0.6.0

and this:

> Copying file po/Makefile.in.in

Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
[ftp://ftp.gnu.org/pub/gnu/config/](ftp://ftp.gnu.org/pub/gnu/config/).

The script with stable 0.5.2 goes a bit more further:

> winrules.c: In function 'winrulesGetAllowedActionsForWindow':
winrules.c:664: error: too many arguments to function 'w->screen->getAllowedActionsForWindow'
winrules.c:665: warning: assignment from incompatible pointer type
winrules.c: In function 'winrulesInitScreen':
winrules.c:753: warning: assignment from incompatible pointer type
make[3]: *** [winrules.lo] Fehler 1
make[3]: Verlasse Verzeichnis '/home/cypher/.compiz-setup/plugins-main/src/winrules'
make[2]: *** [all-recursive] Fehler 1
make[2]: Verlasse Verzeichnis '/home/cypher/.compiz-setup/plugins-main/src'
make[1]: *** [all-recursive] Fehler 1
make[1]: Verlasse Verzeichnis '/home/cypher/.compiz-setup/plugins-main'
make: *** [all] Fehler 2
[Failed] The previous process exited with error 2
cypher@HaeckFlaisch:~$ 

I succesfully used bp-compiz yesterday, so i guess it'an error related to a git-update. Please, if someone does know how to fix it, please submit the changes in bp-compiz.

---

### Post by JackyBoy on 2007-10-22
Hi, I'm getting this error when I run the script:

> checking for COMPIZ... configure: error: Package requirements (x11-xcb          xcomposite               xfixes                  xdamage                 xrandr                  xinerama                ice                     sm             libxml-2.0               libxslt                 libstartup-notification-1.0 >= 0.7) were not met:

No package 'libxslt' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables COMPIZ_CFLAGS
and COMPIZ_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

[Failed] The previous process exited with error 1
 

Is there anything I can do to fix this?  Thanks for your help!

EDIT: I went into synaptic and it says I do have libxslt 1.1.21-2ubuntu2 installed.  I'm still stumped!

---

### Post by SQuark on 2007-11-03
Will there be an option for Xfce?

---

### Post by SQuark on 2007-11-04
> **JackyBoy said:**
> 
EDIT: I went into synaptic and it says I do have libxslt 1.1.21-2ubuntu2 installed.  I'm still stumped!

When you're compiling things yourself, you need the -dev packages. libxslt1-dev will do the trick.

I'm trying to use your script in Xubuntu by choosing the GNOME option. So far I've had to install these extra packages:

```
sudo apt-get install libxslt1-dev xsltproc libglu1-mesa-dev
```

Now I'm getting the same error as shockwaver.

---

### Post by OldGrey on 2007-11-04
Hi

Just tried this which went well until I got this error message:

Insalling Compiz Fusion 's dependencies...
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libcairo-dev is a virtual package provided by:
  libcairo2-dev 1.4.10-1ubuntu4
You should explicitly select one to install.
E: Package libcairo-dev has no installation candidate
E: Failed to satisfy Build-Depends dependency for compiz: libcairo-dev
[Failed] The previous process exited with error 100

Advice please

---

