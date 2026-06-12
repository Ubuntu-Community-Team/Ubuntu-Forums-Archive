---
title: "Ubuntu 16.04 LTS currently; update to Ubuntu 16.04.02 LTS solves Ubuntu Software?"
date: 2017-03-06
forum: Installation &amp; Upgrades
---

### Post by Umgb on 2017-03-06
Ubuntu Software does NOT run under Ubuntu 16.04 LTS, which I currently have. --> would an update to Ubuntu 16.04.02 LTS solve this malfunctioning Ubuntu Software?

---

### Post by howefield on 2017-03-06
> **Umgb said:**
> Ubuntu Software does NOT run under Ubuntu 16.04 LTS, which I currently have. --> would an update to Ubuntu 16.04.02 LTS solve this malfunctioning Ubuntu Software?

There have been many fixes to the Ubuntu Software application, just run the normal updates which will take you to 16.04.2 and you'll get them. 

What's the output of..

```
cat /etc/*-release
```

---

### Post by Umgb on 2017-03-06
Hello UCG,  (ah! Steptoe: those were the days...)

I'm a beginner with Terminal commands. But, here's the output from "cat /etc/*-release":
--------------------------
```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=16.04
DISTRIB_CODENAME=xenial
DISTRIB_DESCRIPTION="Ubuntu 16.04.2 LTS"
NAME="Ubuntu"
VERSION="16.04.2 LTS (Xenial Xerus)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 16.04.2 LTS"
VERSION_ID="16.04"
HOME_URL="http://www.ubuntu.com/"
SUPPORT_URL="http://help.ubuntu.com/"
BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"
VERSION_CODENAME=xenial
UBUNTU_CODENAME=xenialen
```
--------------------------
'Tis quite a misleading list, with both 16.04 and 16.04.2 there. The latter with Xenial Xerus - but that's Klakkity Klak (I think), surely?
If I do indeed already have 16.04.2 LTS, I wonder why Ubuntu Software initially functioned, but no longer so.
--> Then, I would appreciate advice on reactivating this often-useful program.
Thank you.

---

### Post by Umgb on 2017-03-09
Some three days ago, I was given a helpful interim reply to my query. I have yet to find assistance regarding my query with my output listing, which I included.
Being held in limbo is frustrating.

---

### Post by howefield on 2017-03-09
A simple bump once a day, even slightly more often than that is acceptable to move your post back up to the top of the list.

So, showing 16.04.2 is good but have you updated recently ?

```
sudo apt update
```
```
sudo apt upgrade
```

If you still have an issue after that, then try running the Ubuntu Software via a terminal, you'll often get some clues as to what is happening in the terminal output..

```
ubuntu-software
```

---

### Post by Umgb on 2017-03-09
Thank you.
I pasted the command "sudo apt update", but after typing the PW, I received this message: "mgb is not in the sudoers file.  This incident will be reported." I'm sure this can be easily rectified. But, having almost no knowledge of the commands  -- even useful ones --  I would appreciate advice on this problem, too.
--> What is the difference between  "sudo apt update"  and  "sudo apt upgrade"?
Sorry to drag you deeper into the quagmire.

---

### Post by howefield on 2017-03-09
> **Umgb said:**
> I pasted the command "sudo apt update", but after typing the PW, I received this message: "mgb is not in the sudoers file.  This incident will be reported." I'm sure this can be easily rectified. But, having almost no knowledge of the commands  -- even useful ones --  I would appreciate advice on this problem, too.
--> What is the difference between  "sudo apt update"  and  "sudo apt upgrade"?

The update commands ensures that your system is aware of the newest packages versions in order that it will know what to upgrade, the upgrade command will as it implies will install those newer packages.

Do you have other user accounts on the machine ?

---

### Post by Umgb on 2017-03-09
I have two accounts, one of which you already know: "mgb", which has normal rights. The second, "xy", possesses Admin rights. Then, there's "root"... But, Admin rights suffice, surely?

---

### Post by howefield on 2017-03-09
> **Umgb said:**
> I have two accounts, one of which you already know: "mgb", which has normal rights. The second, "xy", possesses Admin rights. Then, there's "root"... But, Admin rights suffice, surely?

So, carry out the update and upgrade from the the xy account to ensure that your system is current.

---

### Post by Umgb on 2017-03-09
Booted with [COLOR=#008000]**xy**[/COLOR] (Admin) account and carried out both update then upgrade. [COLOR=#008000]**Ubuntu Software started successfully**[/COLOR]. BUT: when using the standard [COLOR=#ff0000]**mgb**[/COLOR] account, [COLOR=#ff0000]**starting US was unsuccessful**[/COLOR]. So I ran "ubuntu-software" in the Terminal, which resulted in the blinking white cursor on a new line, but without any prompt. After blinking about 10 times, the cursor remained with no further text appearing. --> Performing this same Terminal command under the xy account had been successful.
So using Admin rights, US functions normally; using [COLOR=#ff0000]**mgb**[/COLOR] (normal rights), **[COLOR=#ff0000]US cannot be started[/COLOR]**.

---

### Post by efflandt on 2017-03-10
If you want mgb to be able to do things that require more privileges (sudo), as xy add mgb to sudo group:```
sudo gpasswd -a mgb sudo
```

---

### Post by howefield on 2017-03-11
> **Umgb said:**
> Booted with xy (Admin) account and carried out both update then upgrade. Ubuntu Software started successfully. BUT: when using the standard mgb account, starting US was unsuccessful. So I ran "ubuntu-software" in the Terminal, which resulted in the blinking white cursor on a new line, but without any prompt. After blinking about 10 times, the cursor remained with no further text appearing. --> Performing this same Terminal command under the xy account had been successful.
So using Admin rights, US functions normally; using mgb (normal rights), US cannot be started.

Irrespective, something is "wrong" with the mgb account, even without admin priveliges you should still be able to open the Ubuntu Software application. The only restriction is that your account won't be able to install anything but you would be prompted for the password belonging to the xy account.

I'd create a test account on the machine (name it whatever you want) from the Admin account.

```
sudo adduser tester
```

Go through the prompts pressing enter for all except the password entry where you should give it one, then switch to that account - can it open Ubuntu Software ?  

```
sudo adduser tester
[sudo] password for hugh: 
Adding user `tester' ...
Adding new group `tester' (1002) ...
Adding new user `tester' (1002) with group `tester' ...
Creating home directory `/home/tester' ...
Copying files from `/etc/skel' ...
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully
Changing the user information for tester
Enter the new value, or press ENTER for the default
	Full Name []: 
	Room Number []: 
	Work Phone []: 
	Home Phone []: 
	Other []: 
Is the information correct? [Y/n]
```

---

### Post by Umgb on 2017-03-11
Thank you, gentlemen, for your replies. I have stored the "sudo" command, a useful one. Regarding the more detailed suggested test account in dealing with **Ubuntu Software not opening** under the **mgb normal-user**, I'm feeling under the weather, but hope to give you feedback within a few days.

---

### Post by Gstrazds on 2017-03-11
[COLOR=#000000]Quote BUT: when using the standard mgb account, starting US was unsuccessful. So I ran "ubuntu-software" in the Terminal, which resulted in the blinking white cursor on a new line, but without any prompt. After blinking about 10 times, the cursor remained with no further text appearing. --> Performing this same Terminal command under the xy account had been successful. endquote

I just had this; In Grub I went back to Ubuntu version ending in 63 under advanced ubuntu options.. which caused the software updaters to work; then re-updated; 

I was also trying to install the Dconf-editor which now will not populate.[/COLOR]

---

### Post by Umgb on 2017-03-13
Well. H, the tester account was able to open Ubuntu Software.
As 16.04.2 LTS has, presumably, addressed the Ubuntu Software problem, I'm inclined to flatten the HDD and re-install this latest version. It'll save us both your time and mine - and save our patience.
Is there anything new that I have to be aware of when installing this latest?

---

### Post by Umgb on 2017-03-13
Thank you, G, for your offer. But I will await H's comment, before making a new installation of the latest LTS.

---

### Post by Umgb on 2017-03-15
An additional snippet of information. 
My Ubuntu has been _sluggish of late_, and today the boot screen (white text on black) showed some text. Unfortunately, I could hardly register what was stated - half a dozen lines, with something about a *journal*.

---

### Post by howefield on 2017-03-15
Well, certainly reinstalling is an option which if well prepared takes not much more than half an hour but it is a sledgehammer approach :)

You could create another account as above and use that, having backed up your important data then copy into the new account. But if the "tester" account is affected by sluggishness also then there is that to consider. Does the performance suffer beyond the boot process ? You might use the disks utility to test the disk.

---

### Post by Umgb on 2017-03-16
Your perseverance  -- and patience --  is appreciated. 
--> I agree about the sledge-hammer method. But, it is an option that is becoming more concrete, with **mgb** being sluggish even after booting. (Can one do a Screen Shot of the boot-screen text?)
I did want to remove some utilities, but, due to not being able to start US, I have to bear with that "braking system"; I imagine that one can do so via Terminal commands, but, I do not know them. Any help in this regard, please?  (I'm building quite a command reference library!)
--> A backup of **mgb**'s "important" data involves copying Home - is that correct?
--> I will check **tester** for any sluggishness.
--> I started the disks utility, but could not find "SMART Data & Self Tests...." on the dear icon, as suggested in GNOME Help. This tells me open Disks from the Activities - this latter nowhere to be found - I simply opened Disks.

---

### Post by howefield on 2017-03-16
> **Umgb said:**
> Your perseverance  -- and patience --  is appreciated. 

You're more than welcome to what little I can offer.

> I agree about the sledge-hammer method. But, it is an option that is becoming more concrete, with **mgb** being sluggish even after booting. (Can one do a Screen Shot of the boot-screen text?)

I guess not easily although you could browse the log files which is found in..

```
/var/log/boot.log
```

> I did want to remove some utilities, but, due to not being able to start US, I have to bear with that "braking system"; I imagine that one can do so via Terminal commands, but, I do not know them. Any help in this regard, please?  (I'm building quite a command reference library!)

Not sure what you are saying here or referring to ?

> A backup of **mgb**'s "important" data involves copying Home - is that correct?

Well, yes. At the least you would want to back up your data, ie Documents, Downloads, Music, Pictures and Videos folder plus any other that you created. You should have this in any event given than one copy of a file is an accident waiting to happen. Taking a copy of your /home folder covers this plus all the configuration files/folders contained therein.

> I started the disks utility, but could not find "SMART Data & Self Tests...." on the dear icon, as suggested in GNOME Help. This tells me open Disks from the Activities - this latter nowhere to be found - I simply opened Disks.

From the "hamburger" menu near the top right corner select "*SMART Data & Self Test*" or use the keyboard shortcut of Ctrl + S.

[ATTACH=CONFIG]274169[/ATTACH]

---

### Post by Umgb on 2017-03-23
I performed all the suggested and posted the results quite some time ago. But, now I see there's nothing to show for it here. Funny.
Firstly, I have executed an update/upgrade. Does this include ALL active apps/programs, such as Firefox?
With   **tester**  , one could start US; this remains impos sible with  **mgb**  and **xy**. Fr  ustrating.
 Disks ran successfully, with nothing untoward to show.
With my unfortunately worded text about removing unnecessary, I had suggested that these might be factors influencing the sluggish nature of the iX running under mgb. As US is unaccessible, I wondered whether this task could be by Terminal commands.

--> In the meantime, I had >60 open tabs in FF, which found it huffing and puffing, working in slow-motion: the screen darkened and one could do nothing but wait a relative age, before considering an exit; that, too, was a long time in coming.

---

