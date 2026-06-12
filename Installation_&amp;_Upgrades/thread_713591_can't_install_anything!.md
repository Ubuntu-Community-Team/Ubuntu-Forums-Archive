---
title: "can't install anything!"
date: 2008-03-02
forum: Installation &amp; Upgrades
---

### Post by marlene on 2008-03-02
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report, is the message I get when I try to download or update.  I've tried all the codes that I've seen in the forum but nothing works. I can't even open Synaptic package manager without getting that message.  I'm starting to regret installing this OS.  What should I do?

---

### Post by Rocket2DMn on 2008-03-02
Open a terminal and run
```
sudo dpkg --configure -a
```
If that doesn't work, please post the output so we can troubleshoot.

---

### Post by marlene on 2008-03-04
root@marlene-desktop:~# sudo dpkg --configure -a
Setting up esound-common (0.2.38-0ubuntu4.1) ...
Setting up gdm (2.20.1-0ubuntu2) ...
 * Reloading GNOME Display Manager configuration...                              * Changes will take effect when all current X sessions have ended.
                                                                         [ OK ]

Setting up libntfs-3g16 (1:1.1120-1ubuntu2~gutsy1) ...

Setting up libk3b2 (1.0.4-2ubuntu1~gutsy1) ...

Setting up gnome-cards-data (1:2.20.3-0ubuntu1) ...
Setting up sun-java6-doc (6-03-0ubuntu2) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] 

THIS IS DRIVING ME CRAZY!!!  I'VE TRIED DOING AS IT DESCRIBES ABOVE BUT IT SAYS IT'S UNSUPPORTED.

---

### Post by Rocket2DMn on 2008-03-04
Try running
```
sudo apt-get autoremove
sudo apt-get clean
sudo apt-get remove sun-java6-doc
```
Then try again.

---

### Post by zvacet on 2008-03-05
You didn´t accept Java  EULA.You can try to  do it by going to the **synaptic>edit tab>fix broken packages** and if that doesn´t work also in synaptic find Java and mark it for reinstall.Hopefully window will pop up and you will check box on the left side and click** forward**.

---

### Post by marlene on 2008-03-05
Ok, so none of those codes worked still get message E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
I can't open synaptic either because I get the same message.
Please, please help me figure this out!

---

### Post by Dunpiel on 2008-03-05
[COLOR="DarkSlateBlue"][COLOR="Navy"][COLOR="Indigo"]Marlene, don't feel bad---I'm in the same boat you are. I just joined yesterday and I'm regretting it as well.
These saps are giving us empty advice and no real solutions...I'm getting the same responses you are and
they're doing nothing.

All I been trying to do is install just ONE program to get it to work...LoL.[/COLOR][/COLOR][/COLOR]

---

### Post by Rocket2DMn on 2008-03-06
Marlene, if you're still getting the java error messages, check out this thread: [http://ubuntuforums.org/showthread.php?t=485156](http://ubuntuforums.org/showthread.php?t=485156) - especially post #3, otherwise proceed as follows:
You can find the download zip file download at [http://java.sun.com/javase/downloads/index.jsp](http://java.sun.com/javase/downloads/index.jsp)  by scrolling down to where it says "Java SE 6 Documentation" and hitting Download.  Save it to the /tmp directory, then open a terminal and run
```
sudo chown root:root /tmp/jdk-6-doc.zip
```
Then try to configure again:
```
sudo dpkg --configure -a
```
If it doesn't display any output, that's good, run
```
sudo apt-get update
sudo apt-get upgrade
```
Otherwise post back with more output please.

@Dunpiel: I'm sorry you're having problems, too.  If there is something specific you need help on, post some links to threads you've started and I'll have a look, otherwise keep trying.  Remember that every problem is different and we are trying our best to help as many people as we can.  We aren't professionals, we are users from the community who volunteer our time to try and help people out.

---

### Post by jimv on 2008-03-06
Try clearing out the updates folder:

In a terminal:

[INDENT]
cd /var/lib/dpkg/updates
sudo rm -r *[/INDENT]

---

### Post by Rocket2DMn on 2008-03-06
> **jimv said:**
> Try clearing out the updates folder:

In a terminal:

[INDENT]
cd /var/lib/dpkg/updates
sudo rm -r *[/INDENT]

Be EXTREMELY careful with that command.  Please make the command
```
cd /var/lib/dpkg/updates
sudo rm /var/lib/dpkg/updates/*
```
Better to use double protection by changing to the directory AND specifying the full path in the command, and don't use the -r (recursive) option as it is not needed in this case.

An announcement was made about the rm command awhile back because of it's incredible ability to screw over your system if used incorrectly, see the message here: [http://ubuntuforums.org/announcement.php?f=73](http://ubuntuforums.org/announcement.php?f=73)

---

