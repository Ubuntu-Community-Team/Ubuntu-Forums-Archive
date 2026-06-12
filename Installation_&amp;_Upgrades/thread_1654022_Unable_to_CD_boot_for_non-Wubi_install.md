---
title: "Unable to CD boot for non-Wubi install"
date: 2010-12-27
forum: Installation &amp; Upgrades
---

### Post by bnyc on 2010-12-27
I've been unable to do a non-Wubi install of U 10.10 desktop 32 bit. My setup:

HP p6240f , Intel® Core™2 Quad Q8300 2.5 GHz, 4 MB L2 Cache, 1333 MHz FSB

Currently, I have a clean install of Windows XP (updated) on my desktop. Previously, I used  a clean install of Windows 7, but ran into the same problems below. My U install problems are:

1.) Live CD will not boot upon restarting PC. As per the U documentation web site ([https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)) , md5sums confirmed that proper .iso copy was downloaded and burned to CD. (However, see log file below for md5 error)

2.) "Installing CD boot helper" does not work. I receive the following error message:
[COLOR=Red]"Could not retrieve the required installation files"[/COLOR], and it refers to a log file. An excerpt of the log file is below.

12-27 18:06 DEBUG  TaskList: #### Finished get_metalink
12-27 18:06 DEBUG  TaskList: New task get_file_md5
12-27 18:06 DEBUG  TaskList: #### Running get_file_md5...
12-27 18:07 DEBUG  TaskList: #### Finished get_file_md5
[COLOR=Red]12-27 18:07 ERROR  CommonBackend: Invalid md5 for ISO C:\ubuntu\install\installation.iso (59d15a16ce90c8ee97fa7c211b7673a8 != 76ff4374b39134c1ca228718c4308ba7)[/COLOR]
None
12-27 18:07 DEBUG  TaskList: ### Finished check_iso
12-27 18:07 DEBUG  TaskList: ## Finished use_cd
12-27 18:07 DEBUG  TaskList: ## Running extract_kernel...
[COLOR=Red]12-27 18:07 ERROR  TaskList: Could not retrieve the required installation files[/COLOR]
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 515, in extract_kernel
[COLOR=Red]Exception: Could not retrieve the required installation files[/COLOR]
12-27 18:07 DEBUG  TaskList: # Cancelling tasklist
12-27 18:07 DEBUG  TaskList: # Finished tasklist
[COLOR=Red]12-27 18:07 ERROR  root: Could not retrieve the required installation files[/COLOR]
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 120, in select_task
  File "\lib\wubi\application.py", line 217, in run_cd_boot
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 515, in extract_kernel
[COLOR=Red]Exception: Could not retrieve the required installation files[/COLOR]

Any help would be greatly appreciated. Thanks.

---

### Post by amsterdamharu on 2010-12-27
I have a couple of quesitons:

[LIST=1]
[*]What does not boot, does it show a black screen where you can type commands or does it show nothing?
[*]Is there any OS booting from that machine and if yes; do you have cabled Internet available?
[*]Do you have a usb stick of about 1 GB available to boot from?
[/LIST]

---

### Post by bnyc on 2010-12-27
Thanks for the prompt reply! My answers are below in blue:

1.) What does not boot, does it show a black screen where you can type commands or does it show nothing? [COLOR=Blue]Nada....no U black screen. Restarting PC goes directly into Windows XP. Boot menu is set so that CD-ROM boot has priority over HDD boot. [/COLOR]

2.) Is there any OS booting from that machine and if yes; do you have cabled Internet available? [COLOR=Blue]OS booting works (by this I assume that you mean if I desire to re-install Windows XP or 7, the PC boots from the CD-ROM). I have cabled Internet.

Previously, I had and tried Easy BCD ([http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)) to boot Live CD, but that did not work. I used to have Windows XP, 7 and Wubi U on separate partitions on my PC. [/COLOR][COLOR=Blue]The foregoing are no longer on my PC...[/COLOR][COLOR=Blue]I wanted non-Wubi U installed on my PC, [/COLOR][COLOR=Blue]erased my HDD and did a complete reinstall of Windows XP.[/COLOR]
[COLOR=Blue]
[COLOR=Black]3.) [/COLOR][/COLOR]Do you have a usb stick of about 1 GB available to boot from? [COLOR=Blue]Yes[/COLOR]

---

### Post by amsterdamharu on 2010-12-27
If you have the iso file I advice you to use a program called [unetbootin]("http://unetbootin.sourceforge.net/") to make the usb run as the live CD. It is available for both Linux and Windows.


Do not choose a distribution as it will try to download the 600+MB iso file, just choose disk image and browse to the iso. Unetbootin should not destroy the data on the usb stick but it depends how important the data is and if you want to take a small risk to loose it. Usb stick needs to be fat16 or fat32 formatted.

---

### Post by bnyc on 2010-12-28
Thanks amsterdam! It worked. During installation, I ran into a problem where the install page would hang on the "Who are you" page and the "Forward" button on that page did not work. After about 4 (fresh) install tries, I finally got U to install on my desktop PC.

Again, thanks for your prompt replies and your advice.

---

### Post by amsterdamharu on 2010-12-28
Well, I suggested to get your existing install working but if re installing works for you than thats fine.
A re install can delete all your personal files on Ubuntu and if you do something wrong it can delete all the Windows files as well so it's a bit of a last resort.

---

