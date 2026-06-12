---
title: "Easiest way to replace Windows10 with Ubuntu"
date: 2022-05-02
forum: Installation &amp; Upgrades
---

### Post by gdpetti2 on 2022-05-02
I want to replace Windows 10 on this new computer. Do I need to make a USB bootable drive for that? I just need to replace Wins10 with Ubuntu. Can't I just download it on Windows and replace it? Is that USB bootable drive necessary?

---

### Post by GhX6GZMB on 2022-05-02
[COLOR=#000000]"Can't I just download it on Windows and replace it?"
[/COLOR]
No. Bootable USB-thumb or DVD, flatten the harddisk and install.
Ubuntu is not an application.

---

### Post by crip720 on 2022-05-02
With Win 10/11 you can install something like an app, it is still Windows but it allows you to use some of Ubuntu, think it is called WSL.  If you do not want Windows then need to download 20.04 or 22.04 Ubuntu, transfer to a USB/DVD and install, this will wipe out Windows, unless you partition.  It is a good idea to use the 'TRY UBUNTU' to make sure all hardware works first, it should, then install and happy Ubuntuing.

---

### Post by GhX6GZMB on 2022-05-02
Dirtiest approach ever.
A dual-boot would be a better option.
Just my opinion.

---

### Post by gdpetti2 on 2022-05-02
Am I supposed to extract it on the USB drive before inserting in the WIndows computer? The Ubuntu tutorial uses BalenaEtcher. Am I suppose to download that on the USB drive to use it?

---

### Post by QIII on 2022-05-02
> **gdpetti2 said:**
> Am I supposed to extract it on the USB drive before inserting in the WIndows computer? The Ubuntu tutorial uses BalenaEtcher. Am I suppose to download that on the USB drive to use it?

What does the tutorial say?  What is the URL to this tutorial?

---

### Post by gdpetti2 on 2022-05-02
[https://ubuntu.com/tutorials/install-ubuntu-desktop#3-create-a-bootable-usb-stick](https://ubuntu.com/tutorials/install-ubuntu-desktop#3-create-a-bootable-usb-stick)
Sounds like it's done thru the USB
 [B]"Select your downloaded ISO, choose your USB flash drive, and then click Flash! to install your image."
Doesn't say where it's installed. On the flash drive that willl then be inserted into the WIndows computer?
[/B]

---

### Post by QIII on 2022-05-02
Just follow the instructions.  Don't try to read anything into them.

You need to install balenaEtcher on your Windows machine.  You need to download the Ubuntu ISO, then start balenaEtcher on your Windows machine.  When balenaEtcher is running, select the source ISO and the target, in this case your USB.  Then click Flash.

---

### Post by gdpetti2 on 2022-05-02
Ok, thanks.... finally got it done. Windows thru me off a few times saying I needed to format the drive... then said 'flash failed'..... I tried again and it worked.

---

### Post by TheFu on 2022-05-03
> **gdpetti2 said:**
> Am I supposed to extract it on the USB drive before inserting in the WIndows computer? The Ubuntu tutorial uses BalenaEtcher. Am I suppose to download that on the USB drive to use it?

If you've installed Windows using a DVD, what the steps below do is to create that installation media (disc or flash drive). It is read-only.

The ISO file downloaded is bootable and contains both a "Try Ubuntu" environment and the installer.  It has to be copied bit-for-bit to the flash drive or DVD disc from the start of the storage to work.  Windows doesn't have any built-in tools which do this, so a special program is needed. There are a large number of those that work and have some safety checks to ensure you don't prematurely wipe Windows.  

All that special copy does is to create the install environment. It doesn't install.
You cannot just copy the ISO into Windows. It doesn't work that way.
You cannot just double-click on the ISO to make it run. It doesn't work that way.

While you can use etcher, there are a number of other popular programs that work too.  Yumi, Rufus, mkusb, VenToy come to mind.  I think Rufus is probably the most popular.  In the old days UNetBootIn was popular, but that tool has fallen out of favor for some reason.

Now, from a Unix/Linux computer, creating the bit-for-bit copy can be accomplished by a number of commands that are built-into the system with just a little knowledge about the way drives and partitions are named.  Since you have Windows, I think you'll likely want to download Rufus and use that tool.  Probably want to watch a recent youtube video that shows how it works first, just to remove any concerns and answer the simple questions rather than waiting hours for someone here to reply.

After you create the flash drive using Rufus (or any other tool you like), insert the flash device into the computer and reboot. Force the computer to boot from that flash device - there's usually a USB-boot menu, then just work through the installation wizard. Let it use the entire disk and that will 100% wipe Windows and any other OS.

I would not suggest you attempt to dual boot. That can cause complexities that aren't easy for someone new to Linux to solve.  Also, it would be helpful of you have a Local LUG (Linux Users Group) and you know when and where they meet, so you can get hands on help if needed.  Many LUGs meet online and that flash drive "Try Ubuntu" facility is handy even if the system refuses to boot Windows or after the Ubuntu install.  I've run from a Try Ubuntu environment for a few days after a HDD crashed. I always have a flash drive with a copy of Ubuntu that can install or boot into the Try Ubuntu environment as an emergency tool.

Youtube is full of how-to videos for Linux stuff.  The programs may change a tiny bit over time, but the major ideas are valid today just like they were 5 yrs ago.  Certainly, search for videos with the specific release 20.04/22.04 that you are using, but also pay attention to the DE - Desktop Environment.  Linux has about 20 popular desktops, so we aren't stuck with just 1 like *that other OS does.*  The default "Ubuntu Desktop" uses Gnome.  There are many others, so be certain to pay attention.  When asking for help, always specify the version and DE to avoid being asked that as the first question.  Getting an answer for the wrong DE isn't always useful.

---

### Post by gdpetti2 on 2022-05-03
Yes, I got it installed. The problem inow is that the Firefox browser isn't the same. Seems like a test model. No search bar beside the address bar. The top doesn't have the "File, Edit, View, History, Bookmarks, Tools, Help"  commands, so I can't Sync it with the older computer. Is this version of Firefox supposed to be this way?

---

### Post by oldfred on 2022-05-03
You have default snap version?

See this for alternative.
[https://ubuntuforums.org/showthread.php?t=2474458](https://ubuntuforums.org/showthread.php?t=2474458)
[https://ubuntuforums.org/showthread.php?t=2474557](https://ubuntuforums.org/showthread.php?t=2474557)

---

### Post by TheFu on 2022-05-03
> **gdpetti2 said:**
> Yes, I got it installed. The problem inow is that the Firefox browser isn't the same.  

There are slight differences in Firefox between Windows and Linux.
When I first switched years ago, settings and preferences were under different menus. That meant I had to mentally tweak any instructions that I found online - even from Mozilla's support, since most instructions are for MS-Windows. Not really a big deal.

The version of Ubuntu being used will determine which firefox you get.  In 22.04, Firefox is a snap package. Snap packages are designed to protect end-users from themselves. It runs inside a "constrained environment" as part of that protection.  Some of the constraints can be relaxed, but many cannot.

Many people avoid using any snaps by getting selected software from other places - not from the default Canonical/Ubuntu repos. There is a way to extend the repositories to get software from 3rd party repos called PPAs.  [https://help.ubuntu.com/stable/ubuntu-help/addremove-ppa.html.en](https://help.ubuntu.com/stable/ubuntu-help/addremove-ppa.html.en) has a good explanation.  It is common to use a few PPAs for software that you may want to get directly from the software team that creates the software.  I think Mozilla has a PPA for the ESR firefox. [https://launchpad.net/~mozillateam/+archive/ubuntu/ppa](https://launchpad.net/~mozillateam/+archive/ubuntu/ppa)  Yep.

In 20.04, Firefox is still a normal APT package.
Chromium switched to a snap in 20.04 and later. There are alternative PPAs that can be used. 

The hard part is determining which of these PPAs are trustworthy. That's no small task since anyone can have a PPA.  You can, if you like. So can I.  If I'm a bad person, I could have my PPA replace some core ubuntu software and provide a back door into your system ... if I liked.  Of course, I'd need for you to both setup my PPA on your system and that system would need to have the software on it.  Say that I picked a nearly universal package for all Ubuntu systems to add my back-door script into?  That's the danger in using any PPA.  Plus, humans make mistakes, so sometimes, even just by accident, a package will break. Depending on the package, the breakage could be trivial, unimportant and fixed with the next update or it could delete every file on the system, effectively wiping the computer.  Those are the 2 extremes for package issues. They apply to any package on any OS, not just ubuntu or Linux, but OSX and Windows too.  About the worst package mistake I've seen is when one of the packages related to booting the OS has a problem for my specific setup, but not many others. Obviously, the teams making the software carefully test it to ensure it doesn't harm our systems, but sometimes, with over 1B systems out there, each just a tiny bit different from the others, they miss some failures possible for odd setups.

I try to limit the PPAs that I use and get them from either people I know and have interacted with or get them directly from the project team for the software. After all, they wrote the code I'm going to run regardless of how it is delivered, so I've already decided to trust them. Their packages too.

If you want an Ubuntu-like experience, but simplified to avoid snaps, there is Linux Mint.  [https://www.linuxmint.com/](https://www.linuxmint.com/) Especially for new people to Linux, it seems to be a fine release. I don't use it, but may switch my desktops over since I'm not a fan of snaps and avoiding them on Ubuntu is becoming harder and harder each release.  I number of people at my LUG use Mint and are happy with it.  The project leader is anti-snap.

---

### Post by Dennis N on 2022-05-03
> **gdpetti2 said:**
> Yes, I got it installed. The problem inow is that the Firefox browser isn't the same. Seems like a test model. No search bar beside the address bar. The top doesn't have the "File, Edit, View, History, Bookmarks, Tools, Help"  commands, so I can't Sync it with the older computer. Is this version of Firefox supposed to be this way?

Search bar like the attachment shows? You have to customize the tool bar to add it: 
Firefox Application Menu > More Tools > Customize Toolbar

Menu bar items are revealed with Alt key.

---

### Post by gdpetti2 on 2022-05-03
Ok.... the Alt key worked. I'llcustomize the tool bar after I figure out which password mozilla wants to sign in to Sync. Maybe I have to setup a different account on the new computer?

---

### Post by ubfan1 on 2022-05-03
Or get to the customize toolbar with a R click on the tool bar and select the customize.

---

### Post by gdpetti2 on 2022-05-03
Problem now is getting the FIrefox Sync setup. THe directions say something else than what happens. On the new computer, I input the same email address, then it changes to Sign in Password required. I try using the password from the old computer, or email address, but they don't work. The directions said it should go to Sync setup account page, but that didn't happen. I have the two computers a couple feet apart on Wifi, is that the problem? If so, wouldn't it accept the password? How does Sync work? Isn't the new computer suppose to setup a new Firefox login account? That isn't happening, it keeps asking for a password, as if I already setup an account on the new computer.

---

### Post by ajgreeny on 2022-05-03
The sign in password needed to sync all your firefox settings is not the one you have for your user account password in Ubuntu.
If you have used firefox sync in the past you must have registered and signed into firefox at some point, then all those settings in use for one instance of firefox will be held presumably in the cloud and sent to a second instance of firefox on another computer when you sign in to firefox on that machine.

I have never personally used this as I keep away from cloud storage of any kind and would not want my firefox information held anywhere outside of my control.
Paranoid? Maybe but I feel more comfortable that way.

---

### Post by gdpetti2 on 2022-05-03
Well, the problem is the new computer won't setup a new FIrefox account for Sync. When I input my email address, the next screen asks for a password. I've tried the SYnc  password from the old computer, but it doesn't work, and I just setup it up an hour ago. I thought I need to setup a different FIrefox account on the new computer to sync them up, but it won't let me do that. Why would it let me set one up on the old computer, but not the new one? They are only a couple feet apart on the same Wifi network.

---

### Post by gdpetti2 on 2022-05-03
Tried many times to import the bookmarks.html file but when I click on it, the 'Select' button on the top right, doesn't change to 'open'..... but I can see the links in the edit bookmark popdown menu. I've tried doing it on USB stick, and in the files, but that Select button won't change to open.

---

### Post by gdpetti2 on 2022-05-03
Ok, found my bookmarks.... seems they download into the bookmarks folder but not to Firefox when opened.... when I clicked on that star next to the + sign...  up on the right side, there are multiple versions of the same categories of bookmarks, probably each time I downloaded that html file... only it never setup to the toolbar. So, now on  to the passwords/logins.

---

