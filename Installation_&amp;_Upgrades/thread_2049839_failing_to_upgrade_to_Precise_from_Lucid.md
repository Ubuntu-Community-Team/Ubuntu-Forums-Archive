---
title: "failing to upgrade to Precise from Lucid"
date: 2012-08-29
forum: Installation &amp; Upgrades
---

### Post by silbar on 2012-08-29
Greetings,

I did a search on "upgrade precise fail" and did not find a thread that seemed like my problem.  Please let me know if there is one.

In trying to upgrade from Lucid 10.4. to Precise 12.04.1 I get the following error messages: 

[INDENT]
root@Lynx:~# apt-get upgrade
Reading package lists... Error!
E: Dynamic MMap ran out of room. Please increase the size of APT::Cache-Limit. Current value: 25165824. (man 5 apt.conf)
E: Error occurred while processing shorewall6-lite (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_universe_binary-i386_Packages
W: Unable to munmap
E: The package lists or status file could not be parsed or opened.
root@Lynx:~# [/INDENT]

I don't know what all this means -- is it really the Cache-Limit?  And, if so, how do I increase it?

R. R. Silbar

---

### Post by irv on 2012-08-29
First, I don't believe you can go from 10.04 to 12.04. I think you need to upgrade to 11.04 first. If you are still in your 10.04, make sure you backup any data you have because doing a upgrade, and if things go wrong you can loose your data files.
My advice to you would be to do a fresh install of 12.04, but first boot with the live DVD/USB and make sure all your hardware is working with 12.04. (Like wifi, Network, Video, etc). Then if it is then install it.

---

### Post by kansasnoob on 2012-08-29
Lucid -> Precise is a valid upgrade path in Ubuntu but apparently not Xubuntu:

[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#Upgrading_from_Ubuntu_10.04_LTS_to_Ubuntu_12.04_LTS](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#Upgrading_from_Ubuntu_10.04_LTS_to_Ubuntu_12.04_LTS)

[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/Xubuntu#Upgrading](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/Xubuntu#Upgrading)

Contrary to what irv said 10.04 -> 11.04 or 11.04 -> 12.04 is NOT a valid upgrade path in either Ubuntu or Xubuntu!

One thing that jumps out at me is this:

> E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_**[COLOR="Red"]univers e[/COLOR]**_binary-i386_Packages

You'll notice that there is an extra space in "universe" so if that was a direct copy-n-paste something appears to be hosed in software sources.

We really need to know what exact method you were attempting to use to upgrade and what flavor of *buntu this is ;)

---

### Post by silbar on 2012-08-29
Kansasnoob asks

> We really need to know what exact method you were attempting to use to upgrade and what flavor of *buntu this is

I first tried from the update manager, and then, with
[INDENT]apt-get update
apt-get upgrade[/INDENT]

From the upgrade manager, things just flash by and it disappears, doing nothing.  The apt-get upgrade gave the error messages in my original posting.

Checking the "Problem with Mergelist", there was no space in the middle of the universe.

This is straight Ubuntu.

   Silbar

---

### Post by silbar on 2012-08-30
OK, but this is really confusing me.

On the advice of a friend who  knows Ubuntu very well, I tried to clean the cache with 
[INDENT]# apt-get clean [/INDENT] 
This completed quickly.  Then I tried again:
[INDENT]# apt-get update [/INDENT] 
This seemed to complete without error (after I restored my last /etc/apt/sources.list file.  Then
[INDENT] #apt-get upgrade[/INDENT] 
also seemed to work properly - it didn't complain, anyway.  But it seemed mostly only to have updated Thunderbird and JRE.  And did not ask me about how /boot/grub/menu.lst should look and didn't ask me to restart!

If I try once more to upgrade either from the Update Manager or the command line, the former disappears at once and the latter says nothing needs to be done, also very quickly

So, this is still being written in Lucid, not Precise.  Does anyone know what is going on here?

R. R. Silbar

---

### Post by silbar on 2012-08-31
I seem to be only talking to myself.  Anybody out there?

OK, I gave up and decided to download the Precise install onto a USB flash drive.  I did so, making it a startup boot device. and adjusted the hardware to boot first from that flash drive, before trying the regular hard disk.  On restart, it did boot from the flash drive, and it looks like 12.04 on the screen.  Good!

So, I then clicked on the "install 12.04" icon, and things proceeded very much like I expected, claiming success at the end.

OK, I removed the flash drive, on the requested restart.  And it booted up into Lucid 10.04.4, NOT Precise!  The grub menu.lst file did not list an Ubuntu 12.04 option!

To see if just copying over that first block in the grub's menu.lst and simply replacing the top line's "Ubuntu 10.04.4 LTS" with "Ubuntu 12.04.1 LTS" does not cure the problem.  It still boots into Lucid.

Any suggestions, anyone?  Thanks in advance,

   Rico Silbar

---

### Post by oldfred on 2012-08-31
If you still have menu.lst that is from grub legacy which was last standard with 9.04. If you upgraded from that then you may have still had the old grub. 

Download this into your USB flash installer and run the BootInfo report. Post link it creates.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

---

### Post by silbar on 2012-09-01
Thanks to oldfred, I've had a lovely (but unproductive) afternoon.  It did sound like he was pointing me to the solution of my upgrade problems.  The chronology of the afternoon follows. This will be long. 

First, working in 10.04, I clicked on the link to Boot-Repair and printed out that web page of instructions.  

I decided to try writing that app to a CD, so I downloaded the 346 MB image "boot-repair-disk-17072012.iso" to my Desktop.  Clicking it to open in Brasero, I started a burn which, unfortunately, ended with an error.  Looking at the save-log did not elucidate what the error was.  So, being stubborn, I tried burning a fresh CD with that image file, and this time it claimed success and ejected..

On re-inserting the CD, it claims to be a 341 GB file system!!!  I suspect MB is a better description than GB.  In looking at the contents of the CD, there is a boot/ directory and other plausible things.  But it wasn't clear to me how to proceed.  Just restart with that CD in place?

So,I decided to try Option 2, i.e., to install Boot-Repair in Ubuntu from the live-USB stick I had made earlier.  Following the instructions, however, the 'apt-get install -y boot-repair && boot-repair' command started out well with many lines of things being done.  But the came up a warning: "0 bytes of disk space remain" and suggested I free up some space.  But, how does one do that?  The USB stick has 16 GB which seems more than adequate.  

So, I clicked on "ignore" and proceeded with the "recommended repair" option, including the "install pastebinit" (whatever that means).  It came soon to a window saying it was "enabling BootInfo" and there it just spun its wheels.  There were evidently some files it could not find.  After a long wait for something to happen, I quit the boot-repair install with a <ctl-C>.

Now what to do?  Was my first installation somehow bungled?  Well, why not try re-installing 12.04 (from the live-USB)?  OK, I tried, and very soon after starting the re-install, I got "System program problem detected".  I did try to report that problem, whatever it was, but apparently nothing was really reported.  A few moments later I got another warning, "ubi-partman crashed."  (This was after I said 'no' to "Unmount sda and sdb disks?"  So, I quit the re-install.

I now figured it was time to get back to 10.04 and to make this posting.  Shutting down and powering up (with the USB stick removed), OMIGOSH!, it gives me a new looking grub menu with 12.04 on top.  And it loads 12.04, indeed, although the log-in window doesn't give me the choice of desktop environment that I see in the 12.04 I have at the Lab.

Now it got scary, because soon after logging in, another "System program problem detected" and "12.04 has an internal error".  Bringing up a terminal window (with <ctl-alt-T>) and doing 'ls -l' on my home directory, none of MY files from 10.04 are there!!!  Have all my files been scrubbed away?

Well, not so, in fact.  Restarting and selecting the 10.04 line from the new grub menu, does get me back to where I was this morning, files intact,  And I am able to send you this long and dismal story.

Thanks anyway, oldfred,

   Rico Silbar

---

### Post by oldfred on 2012-09-01
The only reason Boot-Repair may not finish is if it cannot mount a partition. That can be some corruption somewhere that needs chkdsk on NTFS or e2fsck on the ext family of formats.

Also any download that does not install correctly may be a bad download or bad burn. It can be hard to tell. 
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

The BootInfo should have given a link to you details that you could post we all can see what else may be an issue.

Another way to run just the bootinfoscript which is part of BootInfo.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Boot Info Script 0.61 is released April 2, 2012
boot_info_script.sh" file renamed to "bootinfoscript
[http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/](http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/)
Page with instructions and link to above new download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils

---

### Post by silbar on 2012-09-02
At least, I think so.  I was able to boot into 12.04 and it didn't complain about a "system program problem" this last time.  This is being written from 10.04, however, as there are issues to be resolved before I can use 12.04 effectively.  Again, the last comment from oldfred was very helpful -- thank you.  Here is what I did to get here.

After a restart I seemed to be able to boot into 12.04.  (Was it already booting properly? -- I didn't know.)  

Following the advice on [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair), the second option, I brought up a terminal window (<ctl-alt-T) and successively did the following commands:
[INDENT]sudo -i
add-apt-repository ppa:yannubuntu/boot-repair
apt-get update
apt-get install -y boot-repair
boot-repair
[/INDENT]
This time (perhaps because I was not using the live-USB?) the repair completed successfully.  It also told me to be sure to set the BIOS to boot from the sdb (500 GB) disk.

Looking at what was on the terminal, however, showed there **were** some errors in what boot-repair did.  Mostly failing to find some files, perhaps not fatal, and a warning that it could not create `/root/.local/share/recently-used.xbel' and put some files there.

OK, so I restarted again, into 12.04.  This time (I am not used to where things are in the new desktop environment) I again looked at my home directory.  It was still the generic set of directories, not the set of files I have on 10.04.  This time, however,I noticed on the left side of the browser that it was looking at a 50 GB partition.  There was also a 400 GB partition, which I opened and LO AND BEHOLD, besides /bin/, /boot/, and so forth, I could look into the /home/ and THERE is where my real home directory (10.04) resides.  It was even up to date, as of 11:31 yesterday morning, which was before I began this odyssey into installing 12.04.  

So, nothing is really lost.  I just need to know how to get it to boot to that 400 GB partition.

That was the situation last night.  This morning I booted into 12.04 and tried the advanced options in the boot-repair app.  As oldfred requested, I created a BootInfo summary, which is at [http://paste.ubuntu.com/1181249/]("paste.ubuntu.com/1181249/").  It then quit.

Restarting boot-repair and into advance options, I found the default grub location to be sdb8.  I changed it to place the grub in sdb (as suggested) and applied it.  The new BootInfo summary is at .../1181267/.

Restarting did not change anything -- the home folder was still generic.  Another foray into boot-repair was a dire mistake -- restoring the MBR (master boot record?).  This is summary .../118287/.  On restart, it booted into Windows XP, but without mouse or keyboard!  (Probably because there isn't any XP on this machine, just Vista.)  Eventually Windows decided to crash and restart, which thankfully came up with the usual (new) grub menu and I'm able to get back into Ubuntu.

So, that is why I have rebooted into 10.04 to write this posting.  How do I get things to point to the 400 GB disk and boot from there?

    Rico Silbar

---

### Post by oldfred on 2012-09-02
Your partial numbers to the links do not work. I tried copying the number in and got something weird in pastebin. So I can only see your first run of BootInfo.

You did not select to mount your old /home as part of the install of 12.04, its fstab shows no /home entry for a separate partition like your sdb6 old install (8.04). Your install in sda6 (10.04) does not show a separate /home either. If you want the info from your 10.04 install's /home folder,  you will have to copy the data to your new install or a new partition.

To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

I like to keep /home inside / (root) but have all data in other partition(s). I have a shared NTFS for data I may want to share with XP and a Linux format to share data with my multiple Ubuntu installs.
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

### Post by silbar on 2012-09-07
Sorry, Fred, I failed to notice your response of four days ago -- it was on page 2 of the thread.  As regards the partial links, I assumed that they were always [http://paste.ubuntu.com/xxxxxxxxx](http://paste.ubuntu.com/xxxxxxxxx).

I apologize if this posting sounds like I am only talking to oldfred.  Others may join the fray, if they wish.

Thanks for the pointer to relocating my /home directory to sda6 and the fstab.  Unfortunately, by now I think I have really screwed things up with the 12.04 installation.  Is there an uninstall app?  Or, can I simply re-install it anew from the LiveUSB?

In the meantime, using the boot-repair (with the LiveUSB) I have gotten the grub location set to sda6 and the machine now boots by default into 10.04 with my old /home/ in place.  But the grub menu that comes up has a whole bunch of 2.6 options (all identical?) and no way to get to 12.04 that I can see.

Which does prompt the curiosity question: /boot/grub/ has no menu.lst file (as you pointed out earlier), but where is the menu that comes up generated?

   Rico Silbar

---

### Post by oldfred on 2012-09-07
With grub2 you generate a new menu with
sudo update-grub

That also runs the os-prober that finds other systems to add to the bottom of the menu. If you have a lot of old kernels it may be time to houseclean. They should all be different two each version,  second is recovery. If you have so many, it may fill the menu box and you have to scroll down to see the new install at the bottom of the menu. A tiny arrow on right bottom will tell you that you can scroll down for more entries.

I prefer synaptic to uninstall kernels, but now they do not install synaptic by default. I like to keep two, current & previous just in case.
HOWTO: Remove Older Kernels via GUI (or CLI)
[http://ubuntuforums.org/showthread.php?t=1587462](http://ubuntuforums.org/showthread.php?t=1587462)

#Current kernel:
uname -a
#current install:
lsb_release -a

---

### Post by silbar on 2012-09-07
Yes, thank you once again.  However, on logging in this afternoon, the update manager says there is a new version of the 12.04 upgrade.  Maybe I should try that first?

Rico

One hour later -- I am going ahead with the new upgrade.

---

### Post by silbar on 2012-09-14
One week later:

I won't bore you with everthing that I did wrong (and things that shouldn't have gone wrong). I have "solved" this problem by finally successfully upgrading from a LiveCD disk to 12.04.  This posting is coming to you now from 12.04, and many thanks to this forum for helping me sort out the problems I had in getting to this point.

Rico Silbar (a proponent of the Gordian Knot Solution)

---

### Post by irv on 2012-09-14
Why not mark this one solved.
[ATTACH]224153[/ATTACH]

---

