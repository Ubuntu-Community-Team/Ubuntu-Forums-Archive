---
title: "Upgrade to 12.04: Hangs at boot stage"
date: 2012-11-06
forum: Installation &amp; Upgrades
---

### Post by cozski on 2012-11-06
Hello

I was upgrading my Toshiba Satellite L300 from 11.04 to 11.10 and no problems so decided to just continue to boot to 12.04. The upgrade appeared to go okay until re-boot stage. At this point it is hanging after I get past the Ubuntu splash screen of dots and is informing me that it is checking battery state. Ctr+Alt+Del will start the re-boot process again but I arrive back at the same point. I've looked a few threads with similar problems but not identical and I can't seem to find a fix. I'm not even able to boot into recovery mode, which I believe should be possible by pressing Esc during boot process. 

Any help/advice really appreciated... I really dont want to do an complete re-install if I can avoid it. Thanks in advance.
R.

---

### Post by cozski on 2012-11-11
Hey, any thoughts or suggestions? Anyone? :confused:

---

### Post by bogan on 2012-11-12
Hi!,** cozski,**

Is your set-up a direct install, dual with Windows, or with 'Wubi'??

Can you boot from a LiveCD/UISB ??

Usually, " checking battery state " is followed by "[OK}" and is reporting that the check is complete; as a rule, hanging at that point indicates a video driver problem.

Can you get to a Terminal? 'Ctrl_Alt+F1' or 'Ctrl+Alt+t'?

If so, please Post the output of the following:```
uname -r
lspci -nnk | grep -iA3 vga
/usr/lib/nux/unity_support_test -p
```During the first stage of boot up, following the Bios splash screen, pressing 'Shift' repeatedl, should give you a Grub  boot menu with OS options, including recovery modes. [ In 12.10, Recovery is in a sub-menu titled 'Advanced Options'.]

If you get to the recovery menu, choose the 'drop to root shell' option and enter the code above, line by line.

Chao, **bogan.**

---

### Post by cozski on 2012-11-13
> **bogan said:**
> Hi!,** cozski,**

Is your set-up a direct install, dual with Windows, or with 'Wubi'??

Can you boot from a LiveCD/UISB ??

Usually, " checking battery state " is followed by "[OK}" and is reporting that the check is complete; as a rule, hanging at that point indicates a video driver problem.

Can you get to a Terminal? 'Ctrl_Alt+F1' or 'Ctrl+Alt+t'?

If so, please Post the output of the following:```
uname -r
lspci -nnk | grep -iA3 vga
/usr/lib/nux/unity_support_test -p
```During the first stage of boot up, following the Bios splash screen, pressing 'Shift' repeatedl, should give you a Grub  boot menu with OS options, including recovery modes. [ In 12.10, Recovery is in a sub-menu titled 'Advanced Options'.]

If you get to the recovery menu, choose the 'drop to root shell' option and enter the code above, line by line.

Chao, **bogan.**

Hey, thanks for following up... I will post tomorrow when I get back from work and let you know how I get on with your suggestions... appreciated :)

---

### Post by cozski on 2012-11-19
Hey, apologies for ther delayed reply... work, life, family and all that!

So you were right that it does hang at the stage you suggested. So I press Ctr+Alt+F1 but it then prompts me to login... which I 'think' I do by inserting the password. It then asks for another password which I duly insert but each time it tells me the password is incorrect.

Now, the first passowrd appears to be for the Laptop itself.... I have set a password through BIOS which has remained the same for around 3 years so I know that's right. My password for logging into the OS is also the same password I've used for many years.... now I may be misunderstaning which order of passwords it is prompting me for but I even tried them in the different combination to no avail... very strange... so at the minute I can't get passed these password requests... so any thoughts? Thanks.

---

### Post by bogan on 2012-11-19
Hi!, **cozski**,

In a TTY - Text Terminal - the first login request is for your username, then it asks for your password - even if the username was wrong, eg. if you entered your Password instead of your username. Then, even if the password is correct, it will asks for the complete login again.

Have another go.

Chao!, **bogan.**

---

### Post by cozski on 2012-11-19
> **bogan said:**
> Hi!, **cozski**,

In a TTY - Text Terminal - the first login request is for your username, then it asks for your password - even if the username was wrong, eg. if you entered your Password instead of your username. Then, even if the password is correct, it will asks for the complete login again.

Have another go.

Chao!, **bogan.**

Okay, sounds like a plan.... will try when I get home, fingers crossed ;) thanks.

---

### Post by cozski on 2012-11-21
> **bogan said:**
> Hi!, **cozski**,

In a TTY - Text Terminal - the first login request is for your username, then it asks for your password - even if the username was wrong, eg. if you entered your Password instead of your username. Then, even if the password is correct, it will asks for the complete login again.

Have another go.

Chao!, **bogan.**

Hey, so I managed as per your instructions to boot into recovery mode and this is the output from code you asked me to enter:

3.0.0-26-generic
00:02.0 VGA Compatible Controller [0300] : Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) [80:86:2a03] (rev 03)
no such file or directory

I hope that helps, thanks :)

---

### Post by bogan on 2012-11-22
Hi!,** cozsk**i,

There is something wrong with your 12.04 upgrade, as 'uname -r' shows: "3.0.0-26-generic", which is 11.10. 12.04 would show "3.2.2.0-33 or 34" and the unity_test cmd would have shown the support level.

[ I am assuming that you do not get a Recovery Menu, or that 'Resume normal boot' does not work.]

Do you get a grub boot menu with alternative OS choices?, or is 11.10 the only choice you get?

Can you run: ```
update-manager
``` from a recovery tty?, or does it give you a: 'can not open screen' type message?

If it runs, and updates are available, install them.
Does it give you an "Update to 12.10 available"  message, or similar? If so, run it.

If it does not, then try the following: [the dpkg cmd may take a long time, 10-15 minutes, with no feedback, just wait it out]. 
From a terminal or tty, run the following and reboot.```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get install -fix-missing
sudo dpkg-reconfigure -a
sudo reboot
```Then re-run the previously requested cmds: ```
uname -r 
lspci -nnk | grep -iA3 vga
 /usr/lib/nux/unity_support_test -p
```and Post how you got on.

Edit: A Tip that may help:

If you have a mouse with a middle button or a Scroll Wheel, to copy and paste a command line into a terminal or TTY:
1. Open the terminal.
2. Highlight the cmd line you want to run.
3. Move the Mouse cursor to the prompt in the terminal window.
4. Press the Middle Button or Scroll Wheel; the cmd text will be Pasted into place.
5, Press 'Enter'.

Chao!,** bogan.**

---

### Post by cozski on 2012-11-26
> **bogan said:**
> Hi!,** cozsk**i,

There is something wrong with your 12.04 upgrade, as 'uname -r' shows: "3.0.0-26-generic", which is 11.10. 12.04 would show "3.2.2.0-33 or 34" and the unity_test cmd would have shown the support level.

[ I am assuming that you do not get a Recovery Menu, or that 'Resume normal boot' does not work.]

Do you get a grub boot menu with alternative OS choices?, or is 11.10 the only choice you get?

Can you run: ```
update-manager
``` from a recovery tty?, or does it give you a: 'can not open screen' type message?

If it runs, and updates are available, install them.
Does it give you an "Update to 12.10 available"  message, or similar? If so, run it.

If it does not, then try the following: [the dpkg cmd may take a long time, 10-15 minutes, with no feedback, just wait it out]. 
From a terminal or tty, run the following and reboot.```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get install -fix-missing
sudo dpkg-reconfigure -a
sudo reboot
```Then re-run the previously requested cmds: ```
uname -r 
lspci -nnk | grep -iA3 vga
 /usr/lib/nux/unity_support_test -p
```and Post how you got on.

Edit: A Tip that may help:

If you have a mouse with a middle button or a Scroll Wheel, to copy and paste a command line into a terminal or TTY:
1. Open the terminal.
2. Highlight the cmd line you want to run.
3. Move the Mouse cursor to the prompt in the terminal window.
4. Press the Middle Button or Scroll Wheel; the cmd text will be Pasted into place.
5, Press 'Enter'.

Chao!,** bogan.**

Hey, thanks again for your reply and advice. I'm afraid I'm struggling with this so I'll explain what is happening and maybe you can help futher.

When I boot the laptop I repearedly press Shift in order to get to a GRUB menu. The GRUB menu provides me with 5 options:

Ubuntu, with Linux 3.0.0-26-generic
Ubuntu, with Linux 3.0.0-26-generic (recovery mode)
Previous Linux Versions
Memory Test (memtest86+)
Memory Test (memtest86+, serial console)

As suggested I've selected the recovery mode option, which brings me to the Recovery Menu of:

Resume (resume normal boot)
Clean (try to make free space)
DPKG (repair broken packages)
FailsafeX (run in failsafe graphic mode)
FSCK (check all file systems)
GRUB (update GRUB bootloader)
Network (enable networking)
Root (drop to root shell prompt)
System-summary

I've tried initially to select DPKG and a whole bunch of CMD line stuff scrolls and then ends with the following:

E: sub-process /urs/bin/dpkg returned an error code (2)
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
python-aptdaemon.gtk3widgets : Depends: python-aptdaemon (= 0.43+bzr805-0ubuntu5) but 0.43+bzr697-0ubuntu1.2 is installed
python-aptdaemon.gtkwidgets : Depends: python-aptdaemon (= 0.43+bzr805-0ubuntu5) but 0.43+bzr697-0ubuntu1.2 is installed
E: Unmet dependencies. Try using -f

I also tried 'Drop to root shell prompt' and entered the code you suggested, which produced a huge list of:
W: Failed to fetch http:// prompts before returning to a flasher cursor in CMD line.

Sorry, but I'm quite baffled. I've tried the 'resume normal boot' option but I return back to the original hanging problem. I'm also notsure how I copy and paste the output of code that comes back as I don’t have a mouse connected to the laptop and even if I could copy it I've nowhere to past it to as I'm working off a separate netbook to reply to these posts. Again, any help appreciated. Thanks.

---

### Post by bogan on 2012-11-26
Hi!, **cozski,**

Did you run the Network enable option before dropping to a Root shell, as the 'Failed to fetch hhttp:' Warnings indicate that there was no internet connection.
Failing that succeeding, failed upgrades are always difficult to repair, so:

If you cannot run Update Manager, or it does not give an option to update to 12.10, then as far as I can see, you have no viable alternative apart from a full install, either of 12.04 or 12.10.

It would be a good idea first to try running from  LiveCD/USB.

As to copy/pasting without a mouse, the only way I know of is to use the Edit menu 'Select All' and 'Copy' in a terminal;  activate the Edit Menu with:  'Alt+e', navigate with the Arrow keys and press 'Enter'. Then paste it to a gedit window and transfer it with a Usb flash stick.

But, of course that will not work from a TTY, as it has no menus.

Chao!, **bogan.**

---

### Post by cozski on 2012-12-03
> **bogan said:**
> Hi!, **cozski,**

Did you run the Network enable option before dropping to a Root shell, as the 'Failed to fetch hhttp:' Warnings indicate that there was no internet connection.
Failing that succeeding, failed upgrades are always difficult to repair, so:

If you cannot run Update Manager, or it does not give an option to update to 12.10, then as far as I can see, you have no viable alternative apart from a full install, either of 12.04 or 12.10.

It would be a good idea first to try running from  LiveCD/USB.

As to copy/pasting without a mouse, the only way I know of is to use the Edit menu 'Select All' and 'Copy' in a terminal;  activate the Edit Menu with:  'Alt+e', navigate with the Arrow keys and press 'Enter'. Then paste it to a gedit window and transfer it with a Usb flash stick.

But, of course that will not work from a TTY, as it has no menus.

Chao!, **bogan.**

Hey bogan.... so I was forced to do a complete reinstall after all. I connected the laptop to my modem via adsl and tried to boot from network. All this did was make it hang again and I was forced to swich it off and tried again but the same problem. So unfortunately, depsite your very helpful suggestions and contributions it seems I was unable to resolve the issue. Pretty annoying in the long run, but I'm being stoical. So a new install and upgrade to 11.10 is where I am at.... kinda back to where I started. 

Big thanks again for your help & support. Cheers.
R.

---

