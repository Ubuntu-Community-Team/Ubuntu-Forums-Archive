---
title: "Blank screen after login after upgrade to 12.10"
date: 2012-11-22
forum: Installation &amp; Upgrades
---

### Post by wanderingarticfox on 2012-11-22
I just updated to 12.10 from 12.04, I use a dual boot with Kubuntu, both are 64-bit. Kubuntu is already updated and is what I am writing from.

I still have both OS's in the Grub list but when I boot into Ubuntu I get the login screen and enter my password and then I get nothing but a dark screen with no prompt or anything.

What command do you recommend I try from the Linux Console [LC] if I get there by Tab>3>enter ?:confused:

From the LC I just ran:>>>>turns out this was the LC for Kubuntu****
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

This got some firefox from the 'upgrade' but the problem still exist

additional note that the login screen background and format are look the same as 12.04 and when I click in the login box the cursur does not appear there the screen just recycles; if I just enter my password without it in the 'box' I get the blank screen.

I will try auto clean and remove and report back; also dpkg --configure -a followed by -f instal and --fix-missing install
>>>>Unable to do>>see below

***I just realized that the tab>3>enter was putting me into the LC for Kubuntu

Q? how to open the LC in Ubuntu from either the GRUB menu or the Ubuntu Log-in screen????
If I click the to place the cursor in the login password box the screen just refreshes.

---

### Post by wanderingarticfox on 2012-11-22
How do I get to the LC or terminal from the GRUB menu or the login page?
Keyboard combinations are what I am looking for. Thx:confused:

---

### Post by bogan on 2012-11-23
> **wanderingarticfox said:**
> How do I get to the LC or terminal from the GRUB menu or the login page?
Keyboard combinations are what I am looking for. Thx:confused:Try 'Ctrl+Alt+F1', [or F2-F6]. That should give you a TTY or Text Terminal in Ubuntu.
[If that is the same in Kubuntu I do not know.]

'Ctrl+Alt+F7, should take you back to a GUI screen, or its precursor.'

From the Grub menu, Press 'c', - read the text below - but it gives a very limited choice of commands.

Chao!.** bogan**.

---

### Post by wanderingarticfox on 2012-11-23
Thx Bogan, I actuaally got in via recovery mode and into the LC. 

I have tried several commands and will group them by the out-put that is the same; this is all in the LC. 
----------------------------------------------------------------------
sudo apt-get update  >returns

*a bunch of failed to fetch then*
W: some index files failed to download. They have been ignored, or old ones used instead
not using locking for read only lock file /var/lib/dpkg/lock
unable to write to /var/cache/apt/
package list or staus file could not be parsed or opened
-------------------------------------------------------------------------
sudo apt-get autoclean   >returns

not using locking for read  only lockfile /var/cache/apt/archives/lock
not  using locking for read only lock file /var/lib/dpkg/lock
package list or status file could not be parsed or opened
----------------------------------------------------------------------
sudo dpkg --configure -a   >returns

dpkg:error: unable to access  dpkg status area:Read-only file system
----------------------------------------------------------------------
sudo apt-get -f install
sudo apt-get --fix-missing install
sudo apt-get autoremove
     >all above >retuned

not using locking for read only lock file /var/lib/dpkg/lock
unable to write to /var/cache/apt/
....could not be parsed or opened
----------------------------------------------------------------------

I also noticed that in my GRUB menu that my Kubuntu [is as normal] shows as Ubuntu 12.10(12.10) but that my Ubuntu is just showing Ubuntu and no version.

I looked at the dpkg --help but do not know what if anything would work and did not want to make matters worse.

If I boot into Ubuntu and click on the password block to enter my password the screen just refreshes.
The background looks the same as my 12.04 but it shows 12.10 at the bottom left.:confused:

I could really use some help here, thx

---

### Post by bogan on 2012-11-23
HI1, **wanderingarticfox,**

Did you try pressing 'Ctrl+Alt+F1' from the login screen?

The Read Only/dpkg problem is probably because you went to a terminal from recovery, though it may be something more serious.

The 'failed to fetch' errors suggest your internet was not connected.

If you get the recovery menu, try running 'FSCK' first to set Read/Write before selecting the 'root shell' option, it may work , but recovery is a bit unpredictable in 12.10.

If 'FSCK' hangs without saying: 'finished', press 'Crtl+c', after a pause, it should take you to the root prompt.

Alternatively: 
Try editing the Ubuntu grub menu entry - highlight and press 'e' and put either " text" or "single" after 'ro quiet splash', in the 'Linux boot' line, then press 'Ctrl+x' to boot into a TTY Text terminal login prompt.

Chao!**, bogan.**

---

### Post by wanderingarticfox on 2012-11-23
Most recently I tried>

sudo apt-get install aptitude     and

sudo apt-get install dselect      >both returned the same

W: not using locking for read only lock file /var/lib/dpkg/lock
E: unable to write to var/cache/apt/
E: The package list or status file could not be parsed or open

I do not know the command line/argument to unlock the read-only dpkg files to continue the installation proccess.
Help with the commaand would be greatly appreciated:)

---

### Post by wanderingarticfox on 2012-11-23
Should I think about using a USB jump-drive to reinstall? or repair?
If so does that work the same as a live CD/DVD?:confused:

---

### Post by bogan on 2012-11-24
> **wanderingarticfox said:**
> Should I think about using a USB jump-drive to reinstall? or repair?
If so does that work the same as a live CD/DVD?:confused:A LiveUSB will do exactly the same as a LiveCD/DVD, only somewhat faster.

However, try  pressing 'Ctrl+Alt+F1' from the login screen, before giving up?

Chao!, **bogan**.

---

### Post by wanderingarticfox on 2012-11-24
I will try that key combination and report back.

Would the Alternate ISO give options to repair?

---

### Post by wanderingarticfox on 2012-11-24
I was able to login via Gnome Classic; will try some commands in the terminal and list here:

---

### Post by wanderingarticfox on 2012-11-25
via Gnome Classic I was able to log in and open the terminal. The following is a list of sudo commands I ran with no returns as an out put; meaning there were no options given:

sudo  apt-get update, apt-get upgrade, apt-get dist-upgrade, dpkg --configure -a, apt-get -f install, apt-get --fix-missing install, apt-get autoremove

sudo apt-get autoclean worked it did some cleaning but followed by autoremove it returned nothing

sudo apt-get update-grub prompted to install grub

sudo apt-get install grub was succcessful

sudo grub ls
>Pobing devices to guess BIOS drives. This may take a long time.
**********14 hours later still no return**************
exited back to command line prompt

ran  sudo apt-get install unity
>unity already newest version

entered  root at command line prompt
>root is not currently installed

sudo apt-get install root-system-bin  (as prompted)
>55 packages to install Y then after installation closed and reopened terminal because I had no clue of what if anything I should try via the root-help menu

sudo apt-get --fix-missing install
sudo apt-get autoremove
>removed grub-pc-bin

I am still in Gnome Legacy but will now try to boot into Unity and report back in a while.

---

### Post by wanderingarticfox on 2012-11-25
Most recently I tried:

sudo rm /var/cache/apt/*
>cannot remove /var/cache/apt/archives:Is a directory

sudo rm /var/cache/archives/*
>cannot remove /var/cache/archives/* no such file or directory

sudo apt-get update
>successful

sudo apt-get dist-upgrades
>no upgrades listed

---

### Post by bogan on 2012-11-25
Hi!,** wanderingarticfox**,

So, you can now boot into Gnome Classic via the normal login, no longer get the 'Read Only' messages, and apt-get can update; is that correct?

You did not say if logging in to Unity/Ubuntu was successful or not. Was it??

Please clarify what the current problem is. Is there a problem with Grub??
I do not understand the purpose of some of the commands you report using.

You Posted:> Would the Alternate ISO give options to repair?I cannot answer that as I never used it, nor a LiveCd/USB to repair an installation.

If your original problem of Login refusing your password, [or the Xserver failing to run] still persists, please Post:```
sudo apt-get install linux-headers # see note below.
lspci -nnk | grep -iA3 vga
/usr/lib/nux/unity_support_test -p
sudo apt-cache policy nvidia-current # if nvidia GPU
sudo apt-cache policy xserver-xorg-video-radeon # if ATI/AMD
```The first command is to check if the correct header file is installed, if it is not, that may be the cause of your problem. If it reports the header file is already the latest version, then it is not the problem.

Chao!,** bogan**.

---

### Post by wanderingarticfox on 2012-11-25
Solution/workaround found

In Classic Gnome I went to>User Accounts>logged in as ADMIN
then Unlock and set to auto-login

closed ap and logged-out then switched back to Unity

Restart no log-in page due to above
>system booted into Unity automatically

opened terminal sudo update-grub
>could not find /boot/grub/menu.lst file
>would you like /boot/grub/menue.lst generated for you selected y and {enter}
>done/completed

The only thing is that Ubuntu does not show 12.10 in boot menu like it does for Kubuntu  The system does boot straight into Unity with-out a log-in screen.):P:biggrin:

The origional issue was that when I clicked on the log-in password box the system would just refresh back to that page, the above work-around seems to have bypassed this issue.  Some commands I reported running are from the Kubuntu Forums and a thread titled re:Ubuntu Forum thread. My name is the same with just a slight difference in the spelling.

Thanks for the last bogan I will run them just to make sure of things, currently waiting on Ubuntu One to set-up back-up in Cloud.

---

### Post by bogan on 2012-11-25
Hi!,** wanderingarticfox**,
Good!, Glad you found a workaround.

It would be interesting to know what happens if you Logout and back in again. Does the problem reoccur, or is it solved by the direct auto login?

You Posted:> opened terminal sudo update-grub
>could not find /boot/grub/menu.lst file
>would you like /boot/[COLOR=Red]grub/menue.lst[/COLOR] generated for you selected y and {enter}
>done/completedThat is a reference to Grub-legacy, which in 12.10 should be grub-pc2.00, but you reported that as 'autoremoved'. Still, if it works.....
> The only thing is that Ubuntu does not show 12.10 in boot menu like it does for KubuntuThat is normal in 12.10. It should be followd by: "Advanced Options for Ubuntu", and if you press 'Enter' wth that entry highlighted, you will get a line in which the version number is quoted and one for the Recovery mode.

Chao!,** bogan.**

---

### Post by wanderingarticfox on 2012-11-26
Yes things are working correctly with the auto-log in and it works from restart and from shut-down.

---

