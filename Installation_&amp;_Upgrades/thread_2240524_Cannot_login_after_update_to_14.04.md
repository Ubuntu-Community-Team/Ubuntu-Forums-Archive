---
title: "Cannot login after update to 14.04"
date: 2014-08-20
forum: Installation &amp; Upgrades
---

### Post by alanfolsom on 2014-08-20
I just attempted to run the upgrade from 12.04 to 14.04 on a 64 bit ACER machine, with Ubuntu the only operatingh system installed.

I get to the login screen, but when I login in I get two "System Program Problem Detected" popups, and then a graphical screen which doesnt show any desktop, nor does it respond to any key actions.

If I boot to recovery mode and drop to root shell, I can see two entries in /var/crash:
    _usr_lib_x86_64-linux-gnu_libgtk-3-0_gtk-update-icon-cache-3.0.0.0.crash
    _usr_sbin_cupsd.0.crash

Any ideas what might be causing this?  Did my update not proceed correctly to completion?  

Thanks,

Al

---

### Post by Bashing-om on 2014-08-20
alanfolsom; Hello ;

In the 12.04 install were you using a proprietary graphics driver ? .. My thought is that the proprietary - non ubuntu thing ! - driver got broke in the upgrade process. - you were cautioned by the installer in respect to 3rd party software -.

IF so, will require (re-)building/installing the graphics driver.

[INDENT][INDENT]a place to start
[INDENT][INDENT][INDENT]just a thought
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by alanfolsom on 2014-08-20
I can't recall doing anything like that.  This is a plain system, and was installed on a wiped hard drive last January from the 12..04 LTS CD.  There's really no reason for any unusual graphics drivers that I can recall.

---

### Post by bmullan2 on 2014-08-20
if you can get to a terminal prompt and have network connection then why not try to re-install the ubuntu desktop

I think even at the GUI Login Prompt you can hit <ctrl> <alt> <f1> to get to a text based login screen.   In either case login and at a terminal prompt reinstall ubuntu-desktop.

$ sudo apt-get install ubuntu-desktop

and see if it installs clean again, reboot and try to login?

You also might want to check if your /etc/apt/sources.list file got changed.   During updates Ubuntu will disable/comment-out some repositories and notify you to remember to re-enable them after the install.

For some 3rd party drivers you may need the "partner" repository etc.   Anyway its worth checking.

---

### Post by Bashing-om on 2014-08-20
alanfolsom; all well then !

A hunt'n we will go.

Let's do make sure that the release upgrade is completed:
Booting to a text terminal.
Boot to grub, and at the grub menu, with the latest non-recovery kernel entry highlighted -> press the 'e' key for edit mode -> boot parameters screen, arrow down and across to the terms "quiet splash" and replace them with the term "text" - with out the quotes.
Press key combo ctl+x to continue the boot process to a textual terminal (TTY1).
Login here ( user name and password - no response to screen ! enter the password blindly.
Now let's see what condition the install is in - clearing out any rubish:
```

sudo apt-get autoclean
sudo apt-get autoremove
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get -f install
sudo dpkg --configure -a

```

Now if/ when all that runs clean we can see what results when we attempt to start the desk top from the terminal.

we need something solid to stand on
[INDENT][INDENT]so we can push
[/INDENT][/INDENT]

---

### Post by alanfolsom on 2014-08-20
I'm thinking more and more that the upgrade aborted or failed somehow partway through.  In addition to the login problem above, the Apache server is not starting correctly as it did before.  It didn't do much, just a small internal wiki and a php script serving serial numbers, but it is not accessible even though the system seems to boot.

I created an installation disk and used it to install another 14.04 alongside the one that's failing, and that works correctly.  

I've been using sbackup to backup crucial data to an external harddrive, so if necessary I can wipe, reninstall all the apps, and restore from backup, but it would sure be nice to fiugre out how to recover this attempt at upgrading.
\

---

### Post by Bashing-om on 2014-08-20
alanfolsom : We can do that !

Do as per my post #5 and we 
[INDENT][INDENT][INDENT]come out swinging
[/INDENT][/INDENT][/INDENT]

---

### Post by alanfolsom on 2014-08-20
Bashing-Om:

Much progress.  As soon as I ran the sudo apt-get autoclean it told me that dpkg had been interrupted.  Ran through all the steps, and now my login actually gets to a desktop.

I still get "System Program Problem Detected" pop-ups, with the same two crash files, as well as the gtk crash file with a .upload suffix instead of a .crash suffix, in /var/crash.

 The Apache server is not starting correctly, but I was asked about envvars for Apache, as well as apache2.conf changes, so that may need some investigating.

---

### Post by alanfolsom on 2014-08-20
Crashes appear gone after a power down and reboot.  On to the Apache issue.  (and whatever appears to have broken remote desktop from my windows computer ;( )

---

### Post by Bashing-om on 2014-08-20
alanfolsom; Great !

Appears now the situation is not as dire as it was, huh . ( wheewwhhh).

I have no experience with Apache .. so will await others to chime in here. 
Else and maybe better - if the booting situation is resolved - :
close this thread - solved- and open a new thread on the Apache issue to gain the audience of those who do in fact know what they are doing.

[INDENT][INDENT]there is a wealth of knowledge here
[INDENT][INDENT][INDENT]on the forum[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

