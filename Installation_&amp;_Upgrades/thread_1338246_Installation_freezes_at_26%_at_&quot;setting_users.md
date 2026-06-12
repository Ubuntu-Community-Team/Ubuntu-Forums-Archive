---
title: "Installation freezes at 26% at &quot;setting users and passwords&quot;"
date: 2009-11-26
forum: Installation &amp; Upgrades
---

### Post by Astrals on 2009-11-26
I am trying to install "ubuntu-9.10-alternate-amd64" and every time i try, it freezes at 26% on "finishing the installation, setting users and passwords".

The downloaded iso and burnt cd were both verified with the md5, so no problems there.

I use the encryption for lvm on entire drive.

My motherboard is "asus m4a78 pro"
Ram 4x2gb corsair 800
Using onboard graphics for now.

any help with this will be appreciated, thanks in advance.

---

### Post by dominosultan on 2009-11-30
I have this same issue installing on a laptop (hp tx1001au).  This may seem like a strange way to set-up a server but it's my only 64bit system.

I'm using the official Ubuntu install media sent out through the post.

---

### Post by manny43 on 2009-11-30
maybe you need to increase ram

---

### Post by Astrals on 2009-12-04
I'm sure that 8gig of ram is enough for this.

It just seems from what i have tried to be an issue with certain asus boards.

After it freezes i just wait about 1 minute then reboot system then it's all working.

The only other issue is that my external vantec sata housing for 2 sata drives does not get recognized at all and that runs off the mother board sata connection.

If i install fedora 11 (yes i know it's probably a swear word here, so i apologize now) external sata drive works great, but i left the fedora distro for a more stable distro with allot less updates needed. The f12 distro for me = cow patties.

---

### Post by dhavalbbhatt on 2009-12-04
I had the same issue, however, I just killed the install. I could get in fine and the system ran fine for me, no issues at all (except that my network connection icon would show that I was not connected to the internet, when in fact, I was). Other than that, there were no functional issues for me.

I did re-install my OS though, with the desktop version and that has been working fine too. 

If there are no functional issues, then I would say, keep using your OS.

---

### Post by Astrals on 2009-12-27
> **dhavalbbhatt said:**
> I had the same issue, however, I just killed the install. I could get in fine and the system ran fine for me, no issues at all (except that my network connection icon would show that I was not connected to the internet, when in fact, I was). Other than that, there were no functional issues for me.

I did re-install my OS though, with the desktop version and that has been working fine too. 

If there are no functional issues, then I would say, keep using your OS.


Yes it does seem to work with no issues, i found to get around the no network icon issue install this offline, when it asks to configure your network choose the later option. When you restart your system with internet connected the icon is there working correctly.

I have also tried the ubuntustudio edition this also has the same problem.

Hope this helps.

---

### Post by cozmos9 on 2010-01-02
I thought I had the same problem, but while typing out a reply to this posting, the install actually completed.  It was stuck at 25% for good 20 minutes, I'd say.  HDD was busy the whole time.  I was installing 9.10 server on a virgin Dell poweredge t310.  Having succeeded, I am now going to try installing on raid 1.

---

### Post by kyriakides on 2010-01-10
The reason you think it hangs is because of a dd process which is copying zeros to the swap space partition. If you switch terminal (Alt-F2) and run a "ps" command you can see the pid of the dd process. You can then check the progress of the dd command in the file /proc/<pid>/io. You need to wait several minutes for it to finish. For example, if your swap is around 5Gb it will take some time (maybe 15 minutes or so) to fill it up with zeros.
 The progress bar message should change to indicate this somehow I think.

---

### Post by Astrals on 2010-01-15
> **kyriakides said:**
> The reason you think it hangs is because of a dd process which is copying zeros to the swap space partition. If you switch terminal (Alt-F2) and run a "ps" command you can see the pid of the dd process. You can then check the progress of the dd command in the file /proc/<pid>/io. You need to wait several minutes for it to finish. For example, if your swap is around 5Gb it will take some time (maybe 15 minutes or so) to fill it up with zeros.
 The progress bar message should change to indicate this somehow I think.


When I installed it, I let it go for over an hour and still stuck at 26%.

I'll do a reformat just to see if it does eventually sort itself out and post my results here (samsung 750GB HD).

EDIT:
Sorry to say but absolute bull**** for my findings.. 4 hours later still hanging at 26%, now writting zero's to swap space does not take that long.
The installation iso (which I have downloaded several times and verified) has issues for amd64 systems using asus motherboards..
When it hangs at 26% I would give it 5 minutes then force reboot (CNTRL+ALT+DEL), it will work fine then.
Also install offline so my network manager recognizes and works, giving me control instead of no control with internet.

I hope this helps.

---

### Post by ats85 on 2010-01-18
I had this problem with my install too. I checked the /proc/<dd PID>/io file and the dd command finished copying but did not terminate, so after about a half hour I just typed 

kill -9 <dd's PID>

and then my install finished in about 15 seconds. Haven't really had any issues since then.

---

### Post by Sgt_P on 2010-01-28
Not sure if this will help, but I had the same problem when using the 64-bit alt-install AND chose to encrypt my home directory. If I chose "no" when prompted to encrypt my home directory it sails right through to the end without a problem.
 
Now if I could figure out what about encrypting the home directory is freezing the install....

---

### Post by ryangsteele on 2010-02-26
> **Astrals said:**
> When I installed it, I let it go for over an hour and still stuck at 26%.

I'll do a reformat just to see if it does eventually sort itself out and post my results here (samsung 750GB HD).

EDIT:
Sorry to say but absolute bull**** for my findings.. 4 hours later still hanging at 26%, now writting zero's to swap space does not take that long.
The installation iso (which I have downloaded several times and verified) has issues for amd64 systems using asus motherboards..
When it hangs at 26% I would give it 5 minutes then force reboot (CNTRL+ALT+DEL), it will work fine then.
Also install offline so my network manager recognizes and works, giving me control instead of no control with internet.

I hope this helps.

Um, and you're surprised your results don't match everyone else's?  There are many variable factors affecting the duration of this operation, such as how fast the disks motor is, how big the swap space is, the manner in which bits are stored on the disk (i.e., perpendicular vs. horizontal), where the inodes for the swap space are physically located on the disk (contiguous vs. non-linear), the size of the platters, and on and on.  Expecting all of these factors to be equivalent to someone else's is a pretty big (and unlikely) assumption.  If you're doubting whether or not the process is active or defunct, ps will tell you that, and so will a multitude of other tools (such as strace).

---

### Post by whatdoesitwant on 2010-03-04
I had this issue as well. It happened when i reinstalled ubuntu server 9.10 32bits. I opted to encrypt the drive. It's an old asus pc, the hdd is about 80gb (maxtor pata, 2006). I had to wait for approx. 35 minutes. So the writing of the 0's seems to differ. Hope this helps.

---

### Post by billzeeabob on 2010-03-08
I have had the same problem on both 32-bit server and desktop installs. Always when I chose to encrypt the home directory. Turn off the encrypting of the home directory everything works fine. 

I am currently installing a new server and wanted an encrypted home. I did the alt-f2 and could not see a problem. I then for fun checked alt-f3 and alt-f4. 

Under alt-f4 I found the system messages which stated the system was scheduled for a restart and everything looked finished. 

I restarted and life is good... sort of.. I really get nervous when an install on a server box does not go as it should. 

Does anyone know who best to get this to for fixing?

---

### Post by apperception on 2010-06-30
When I hit alt-f4, the system messages made it appear as though it was doing some sort of USB probing related to my Logitech USB mouse.  After about 20 mins of this it popped out the CD-ROM and gave me the option of rebooting into the OS.

---

