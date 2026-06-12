---
title: "Computer reboots randomly"
date: 2007-02-10
forum: Installation &amp; Upgrades
---

### Post by rgeddes on 2007-02-10
I've been upgrading my system regularly according to the synaptic update manager... usually 'security' updates on edgy.  My system was fairly stable until a few weeks ago... my system would freeze, requiring a hardware reboot.  I did try to Ctrl-Alt-F1 to get to another login prompt, but the system would not respond.  This behavior continued until the next upgrade... now my system randomly reboots itself with high frequency... this is annoying to me.  I was willing to put up with the occasional freeze, but reboot every few hours... thats for the birds.  This last time, I was downloading something with azureus, the system rebooted without warning, and now azureus will not load... it goes through some initialization, then disappears.    I used 'find' to look for core dumps but found none.  

Can anyone help me troubleshoot this feature on my system?

Thanx
Rich

---

### Post by Matt Yun on 2007-02-10
Well, the culprit is probably Azureus (I dislike it myself; I just use good ol' btlaunchmanycurses).  But if your system is rebooting randomly regardless of the program, that usually indicates a hardware problem.

Possible sources of failure:  cpu fan (if it is unusually noisy, then it is probably defective), power supply (especially no-name models), RAM

---

### Post by rgeddes on 2007-02-11
mmm.., yes I thought of that as well..  my system is a dual-booter (Liin/Win) and the Win side doesn't show the same signs... I'm assuming that if they are using the same hardware (except for the disk partitions) and Win is ok and Lin is not, (except for those partitions) the hardware should be ok.  

Before I assume the partitions are the cause (the long fix), I'd like to explore the possibility that something got scrambled on my hard disk from all those forced reboots.  I'd like to get confirmation of what is the root of the problem.

Is there a way to run in a 'debug' mode so that when something breaks, I can refer to a log file to get a better fix what is breaking.

Thnx
Rich

---

### Post by finer recliner on 2007-02-11
next time it reboots, take note of the exact time.

go to system > administration > system log.

 copy anything that happened right before the reboot to the forum

---

### Post by budgie9 on 2007-02-11
I would suggest you also check your memory with the Memtest86 software on the CD, or downloadable. It is common for a fault in memory, that perhaps just needs reseating to cause these symptoms.

---

### Post by rgeddes on 2007-02-13
I ran the Win2k side of my dual boot Win/Lin system since 8 PM yesterday and all last night (downloading a torrent) doing my usual activities firefox, thunderbird, openoffice, gaim.... no problem.  Tonight i'll run the memory test to be certain ... let it run all night.

I was mistaken when I said reboot... it actually does not reboot, instead i'm taken to the login screen.

Also, I started checking my hard disk after every freeze/relogin by booting from the livecd and running the appropriate fsck's... my boot (/boot) partition is ext2 (for speed), and my root (/) partition is reiserfs (for speed and journaling)

The first time i checked the hard disk, reiserfsck reported 4 corruptions and i corrected them.
I'm not too sure about  the ext2 partition... i ran fsck -f /dev/hdb1.  It output a checklist of items, but no real message of corruptions found.... so i checked the return status (echo $?) and it was 1... so I ran fsck -f /dev/hdb1 until the return value was 0....  I do this every time my system freezes/relogins.... after finding and correcting the corruptions on my root partition, my system no longer sends me to the login screen... it just freezes now, which is what i noticed initially.

As for logs, the last time my system froze, "Feb 12 18..."  I searched all logs with

sudo grep '^Feb 12 18' /var/log/*

and grep returned nothing.

When I ran

sudo grep '^Feb 12 17' /var/log/*

grep returned this:

auth.log:Feb 12 17:09:01 rg-desktop CRON[8298]: (pam_unix) session opened for user root by (uid=0)
auth.log:Feb 12 17:09:01 rg-desktop CRON[8298]: (pam_unix) session closed for user root
auth.log:Feb 12 17:17:01 rg-desktop CRON[8457]: (pam_unix) session opened for user root by (uid=0)
auth.log:Feb 12 17:17:02 rg-desktop CRON[8457]: (pam_unix) session closed for user root
auth.log:Feb 12 17:39:02 rg-desktop CRON[8842]: (pam_unix) session opened for user root by (uid=0)
auth.log:Feb 12 17:39:03 rg-desktop CRON[8842]: (pam_unix) session closed for user root
messages:Feb 12 17:10:46 rg-desktop -- MARK --
messages:Feb 12 17:30:48 rg-desktop -- MARK --
messages:Feb 12 17:50:49 rg-desktop -- MARK --
syslog.0:Feb 12 17:09:01 rg-desktop /USR/SBIN/CRON[8299]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
syslog.0:Feb 12 17:17:01 rg-desktop /USR/SBIN/CRON[8458]: (root) CMD (   run-parts --report /etc/cron.hourly)
syslog.0:Feb 12 17:30:48 rg-desktop -- MARK --
syslog.0:Feb 12 17:39:02 rg-desktop /USR/SBIN/CRON[8843]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
syslog.0:Feb 12 17:50:49 rg-desktop -- MARK --


The only strange (to me) thing I notice is that there is a command in uppercase (/USR/SBIN/CRON) ... not sure what to make of those log entries.  If anyone can read these tea leaves I'd appreciate the interpretation

Thnx
Rich

---

### Post by IgnorantGuru on 2007-02-13
I'm no expert, but if it's going back to the login screen it sounds like something is killing or restarting the X server - same as deliberately doing it with Ctrl-Alt-Backspace.  Maybe the /var/log/Xorg.0.log would show something in that case.

Could be related to a video driver upgrade as well - maybe try uninstalling and reinstalling, or if it's proprietary, try switching to the open driver (if ATI, change "fglrx" to "ati" in xorg.conf.  If NVidia, change "nvidia" to "nv").  Then see if it does it.  I have found the proprietary drivers can cause lockups and other mysterious problems like that.

Beyond that, I would probably reinstall from scratch (backup your home folder so you don't have to reconfigure all your settings and software.  Also back up /etc/fstab and /etc/exports.  Beyond that, there isn't much you'll need to do after reinstalling except restore your /home folder and install additional software.

Then backup the partition so if it happens again you can roll it back, and you can test upgrades more easily.  Howto: [http://www.ubuntuforums.org/showthread.php?p=2148017#post2148017](http://www.ubuntuforums.org/showthread.php?p=2148017#post2148017)

---

### Post by rgeddes on 2007-02-15
I ran the memory test for 9 hours last night... no errors... glad to see the hardware is good... running W2K w/out problems on the same memory confirms this.

I did look into the /var/log/Xorg.* files.  They have a different format than the usual log files.  It seems that they record events on initialization of the video system.

I have an ATI card ... from lspci I get 

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 If [Radeon 9000] (rev 01)
01:00.1 Display controller: ATI Technologies Inc Radeon RV250 [Radeon 9000] (Secondary) (rev 01)

In all the Xorg.* log files I found this message

error opening security policy file /usr/lib/xserver/SecurityPolicy

so I checked myself and, sure enough, there wasn't even a /usr/lib/xserver directory.

So I ran find to look for the SecurityPolicy file:

sudo find / -xdev -type f -name 'SecurityPolicy'

and found it here

/usr/share/doc/xserver-xorg-core/SecurityPolicy

Looking for the source of this problem, I assumed an X config file was referencing the non-existant directory, so I set out to find the offending config file by grepping for 'SecurityPolicy' in all those files:

sudo grep -lr 'SecurityPolicy' /etc/X11/*

and found the pattern in /etc/X11/X  which turned out to be a binary.... can't edit a binary..  so I decided to feed the beast what it wanted... by creating the directory /usr/lib/xserver 

sudo mkdir /usr/lib/xserver

and made a symbolic link to the file in question in the new directory

sudo ln -s /usr/share/doc/xserver-xorg-core/SecurityPolicy /usr/lib/xserver/

rebooted... error message did not show up in the Xorg log file... let's see what happens now.

---

### Post by IgnorantGuru on 2007-02-15
That's the correct solution to the SecurityPolicy error, although I doubt that was the source of your problem.

FYI, I was getting lockups and bad behavior on my laptop with the canned ATI driver.  So I removed the driver and linux-restricted-modules, downloaded the latest driver from ATI's website, and used Method 2 here...
[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

That cleared up most of the instability for me.  (Haven't tried that with the new -11 kernel yet, but it should work.)

---

### Post by rgeddes on 2007-02-27
Thanks for your input...

my system is back up and running 'descently' now.  Normal application crashes and infrequent os freezes (probably once every 5 days.. something I can live with)

What I did:

I decided my hardware is partially to blame:
1997 vintage P3 500 MHz  with motherboard of that era, upgraded w/ 512MB memory, 2 internal (ATA) hard drives, and a Radeon 9000 Pro.  The upgrades are probably exceeding the motherboard capacity to service them.  

Every time I 'reseated' the hard drives, I'd pull on the ribbon cables and  re-attached them.  This, I think, contributed to my problems, possibly affecting the integrity of the cables, as my system seemed to get worse as time went on.  The puzzle was that Windows didn't seem to mind, whereas Ubunutu would freeze or send me to the login screen within an hour of startup.

I purchased a set of expensive ribbon cables ($8 ea) and was very careful installing them.  My system has been much better since.  

I suspect the video card has something to do with it, but I have nothing to back that up.  

I did try to change my video driver the several different ways that are mentioned on the internet, but neither of them worked.  I think Radeon has to take the lead in opening up their source code and/or making their hardware architecture available to get some descent drivers.

Could there be timing issues related to the video display that depend on the hard disk performance?

Thnx again
Rich

---

