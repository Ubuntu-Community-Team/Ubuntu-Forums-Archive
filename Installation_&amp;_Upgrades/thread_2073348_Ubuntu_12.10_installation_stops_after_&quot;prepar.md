---
title: "Ubuntu 12.10 installation stops after &quot;preparing to install ubuntu screen&quot;"
date: 2012-10-19
forum: Installation &amp; Upgrades
---

### Post by anyone2009 on 2012-10-19
Hi guys I have downloaded the Iso file and checked the md5checksum and everything OK,
Firstly I burn it into a dvd and try to install it when I press the "continue" button in this screen [http://www.ubuntu.com/sites/www.ubuntu.com/files/active/02_ubuntu/desktop-1204-install-2.jpg](http://www.ubuntu.com/sites/www.ubuntu.com/files/active/02_ubuntu/desktop-1204-install-2.jpg)

the installation process stops, then I burn it again into a usb flash and the same problem happen again :( 
any help please ?

---

### Post by nelson2006 on 2012-10-19
Yep, having the same problem. Downloaded it twice, burn it on dvd-r and a dvd-rw and the same thing. This is getting me pissed off. I'll try the Ubuntu Gnome Remix 12.10 and see how it goes...

---

### Post by sysmatck on 2012-10-19
I guess I found the solution! Some says to uninstall the ubiquity-slideshow-** But for me did not solve!

searching on /var/log/syslog I found:

Oct 19 15:59:13 lubuntu kernel: [ 2079.442743] gspca_main: ISOC data error: [2] len=0, status=-71
Oct 19 15:59:13 lubuntu kernel: [ 2079.474750] gspca_main: ISOC data error: [17] len=0, status=-71
Oct 19 15:59:13 lubuntu kernel: [ 2079.506740] gspca_main: ISOC data error: [25] len=0, status=-71
Oct 19 15:59:13 lubuntu kernel: [ 2079.542737] gspca_main: ISOC data error: [1] len=0, status=-71
Oct 19 15:59:13 lubuntu kernel: [ 2079.574754] gspca_main: ISOC data error: [24] len=0, status=-71
Oct 19 15:59:13 lubuntu kernel: [ 2079.639601] camerasrc-real-[8840]: segfault at 8 ip 00007f136781f338 sp 00007f134c939b38 error 4 in libgstreamer-0.10.so.0.30.0[7f13677cc000+de000]
Oct 19 15:59:13 lubuntu kernel: [ 2079.642756] gspca_main: ISOC data error: [8] len=0, status=-71
Oct 19 15:59:13 lubuntu kernel: [ 2079.674790] gspca_main: ISOC data error: [31] len=0, status=-71
Oct 19 15:59:25 lubuntu install.py: Exception during installation:
Oct 19 15:59:25 lubuntu install.py: Traceback (most recent call last):
Oct 19 15:59:25 lubuntu install.py:   File "/usr/share/ubiquity/install.py", line 712, in <module>
Oct 19 15:59:25 lubuntu install.py:     install.run()
Oct 19 15:59:25 lubuntu install.py:   File "/usr/share/ubiquity/install.py", line 107, in run
Oct 19 15:59:25 lubuntu install.py:     'START', self.start, self.end, 'ubiquity/install/title')
Oct 19 15:59:25 lubuntu install.py:   File "/usr/lib/python3/dist-packages/debconf.py", line 62, in <lambda>
Oct 19 15:59:25 lubuntu install.py:     lambda *args, **kw: self.command(command, *args, **kw))
Oct 19 15:59:25 lubuntu install.py:   File "/usr/lib/python3/dist-packages/debconf.py", line 67, in command
Oct 19 15:59:25 lubuntu install.py:     self.write.flush()
Oct 19 15:59:25 lubuntu install.py: IOError: [Errno 32] Broken pipe
Oct 19 15:59:25 lubuntu install.py: 

The problem was not the slideshow itself, it was the "take picture" function after user and password configs...

So, I tricked the system opening the GUVCViewer (an webcam viewer); Somehow they compete to get the webcam resource, and then I can move forward flawlessly...

---

### Post by sysmatck on 2012-10-19
I forgot to say: I'm on Lubuntu 12.10 amd64

I guess you guys with ubuntu will need to search the default webcam viewer or install the GUVCViewer

I guess tricking the system not to recognize the webcam will also work.

---

### Post by anyone2009 on 2012-10-19
> **sysmatck said:**
> I guess I found the solution! Some says to uninstall the ubiquity-slideshow-** But for me did not solve!

searching on /var/log/syslog I found:

Oct 19 15:59:13 lubuntu kernel: [ 2079.442743] gspca_main: ISOC data error: [2] len=0, status=-71
Oct 19 15:59:13 lubuntu kernel: [ 2079.474750] gspca_main: ISOC data error: [17] len=0, status=-71
Oct 19 15:59:13 lubuntu kernel: [ 2079.506740] gspca_main: ISOC data error: [25] len=0, status=-71
Oct 19 15:59:13 lubuntu kernel: [ 2079.542737] gspca_main: ISOC data error: [1] len=0, status=-71
Oct 19 15:59:13 lubuntu kernel: [ 2079.574754] gspca_main: ISOC data error: [24] len=0, status=-71
Oct 19 15:59:13 lubuntu kernel: [ 2079.639601] camerasrc-real-[8840]: segfault at 8 ip 00007f136781f338 sp 00007f134c939b38 error 4 in libgstreamer-0.10.so.0.30.0[7f13677cc000+de000]
Oct 19 15:59:13 lubuntu kernel: [ 2079.642756] gspca_main: ISOC data error: [8] len=0, status=-71
Oct 19 15:59:13 lubuntu kernel: [ 2079.674790] gspca_main: ISOC data error: [31] len=0, status=-71
Oct 19 15:59:25 lubuntu install.py: Exception during installation:
Oct 19 15:59:25 lubuntu install.py: Traceback (most recent call last):
Oct 19 15:59:25 lubuntu install.py:   File "/usr/share/ubiquity/install.py", line 712, in <module>
Oct 19 15:59:25 lubuntu install.py:     install.run()
Oct 19 15:59:25 lubuntu install.py:   File "/usr/share/ubiquity/install.py", line 107, in run
Oct 19 15:59:25 lubuntu install.py:     'START', self.start, self.end, 'ubiquity/install/title')
Oct 19 15:59:25 lubuntu install.py:   File "/usr/lib/python3/dist-packages/debconf.py", line 62, in <lambda>
Oct 19 15:59:25 lubuntu install.py:     lambda *args, **kw: self.command(command, *args, **kw))
Oct 19 15:59:25 lubuntu install.py:   File "/usr/lib/python3/dist-packages/debconf.py", line 67, in command
Oct 19 15:59:25 lubuntu install.py:     self.write.flush()
Oct 19 15:59:25 lubuntu install.py: IOError: [Errno 32] Broken pipe
Oct 19 15:59:25 lubuntu install.py: 

The problem was not the slideshow itself, it was the "take picture" function after user and password configs...

So, I tricked the system opening the GUVCViewer (an webcam viewer); Somehow they compete to get the webcam resource, and then I can move forward flawlessly...

thanks guys for your replies ,

I did uninstall "ubiquity-slideshow-ubuntu"
then install GUVCViewer and open it , the webcam was recognized then I try to install ubuntu and the same problem happen :(

---

### Post by sysmatck on 2012-10-19
Try to disable the webcam...
see: [http://askubuntu.com/questions/166809/how-can-i-disable-my-webcam](http://askubuntu.com/questions/166809/how-can-i-disable-my-webcam)

ps: I did not test, because my installation worked!

---

### Post by anyone2009 on 2012-10-19
> **sysmatck said:**
> Try to disable the webcam...
see: [http://askubuntu.com/questions/166809/how-can-i-disable-my-webcam](http://askubuntu.com/questions/166809/how-can-i-disable-my-webcam)

ps: I did not test, because my installation worked!

Thanks for reply but unfortuntly it's not working too, I think it's not a webcam problem BTW I attached the syslog file (I had to compress it because of attatchments issues ) so you can see it.
Note: I plug another usb flash memory to take that file

---

### Post by xtremo on 2012-10-19
> **nelson2006 said:**
> Yep, having the same problem. Downloaded it twice, burn it on dvd-r and a dvd-rw and the same thing. This is getting me pissed off. I'll try the Ubuntu Gnome Remix 12.10 and see how it goes...

I tried Xubuntu....but just the same.....failing on the wifi setup screen.

---

### Post by anyone2009 on 2012-10-20
anyone have a solution ?

---

### Post by xtremo on 2012-10-20
Yeh....I'm still waiting as well. Never happened on any other release I've used.

---

### Post by sysmatck on 2012-10-20
My was crashing forward, but I could get the problem you guys are facing with a virtual machine...
Looking on the syslog, I saw something complaining about NTFS partition...

On my tests, trying to install with an HD with windows installed made the screen to stop, not freeze, but the installation deadlocked on that point. With a blank HD no problem!

Can you guys check that? Can you guys use gparted before installing? Can you guys wipe your discs to install it?

---

### Post by xtremo on 2012-10-20
I've tried with a formatted drive and replacing 12.04 both with Ubuntu and Xubuntu.....and nothing works.

---

### Post by sysmatck on 2012-10-20
> **xtremo said:**
> I've tried with a formatted drive and replacing 12.04 both with Ubuntu and Xubuntu.....and nothing works.

Check your syslog with "tail -n 40 /var/log/syslog" if possible post it like anyone2009 did!

---

### Post by xtremo on 2012-10-20
Got it installed! More by luck than anything else!

I threw in a Debian CD which failed to install.....then put 12.10 back in again and it went straight through the install process. :)

---

### Post by sysmatck on 2012-10-20
> **xtremo said:**
> Got it installed! More by luck than anything else!

I threw in a Debian CD which failed to install.....then put 12.10 back in again and it went straight through the install process. :)

I can't even imagine how that worked... Debian installer is ubiquity too?

---

### Post by anyone2009 on 2012-10-21
> **xtremo said:**
> Got it installed! More by luck than anything else!

I threw in a Debian CD which failed to install.....then put 12.10 back in again and it went straight through the install process. :)

I didn't get it would you please explain ?

---

### Post by xtremo on 2012-10-21
I've got no explanation for it either. I just tried to do a Debian install which crashed before it finished, then when I tried 12.10 again it installed.

Maybe it's because it completely wiped the drive?

---

### Post by xtremo on 2012-10-21
Update to this......I just tested it again. Tried to reinstall 12.10 over 12.10 and failed.

Put in Debian....let it wipe the drive, create partitions, then killed the install.

Then a fresh install of 12.10......and in it went.

So it seems to be if you have a clean drive or a failed install to be written to, there's no problem.

No idea why....that just seems to be the way it is.

---

### Post by sysmatck on 2012-10-21
So... you guys know how to set partitions manually? I mean, no need to cfdisk; a gParted or another GUI partition editor might be ok!

LiveCD uses to came with some of those partitions managers, I've got gParted on Lubuntu live... if you guys don't then "sudo apt-get install gparted"

---

### Post by xtremo on 2012-10-21
> **sysmatck said:**
> So... you guys know how to set partitions manually? I mean, no need to cfdisk; a gParted or another GUI partition editor might be ok!

LiveCD uses to came with some of those partitions managers, I've got gParted on Lubuntu live... if you guys don't then "sudo apt-get install gparted"

Yes....I know how to do that.....but I wanted to recreate the steps I did earlier to see if that would work a second time.

I then did a normal install on the desktop....no problems at all. But that doesn't have a webcam so I'm sure it's related to that.

---

### Post by sysmatck on 2012-10-21
Yeah the webcam thing was a mistake... I tought you guys were stuck on the same screen as I. But I was much further, actually, my installation was crashing, the GUI was closing after user and password configs.. and no thread had the solution, so, it might be usefull for documenting anyway!

---

### Post by anyone2009 on 2012-10-22
then If I clean a partition it's gonna be solved ?

---

### Post by n.masarone on 2012-10-22
Hi all,
after two days fighting against installation stop after "preparing to install ubuntu screen" I solved the situation with following steps (may be some of them are not mandatory, but I used this way):

[LIST]
[*]launch a live DVD with XUBUNTU 12.10, as a trial run
[*]disable disk auto-mount from settings panel
[*]use GPart in order to shrink the existent XUBUNTU partition (already 12.10) and to obtain a new empty partition with EXT4 (on the same disk I have Windows Vista in another partition and a swap partition for Linux)
[*]after this last attempt I could finally install XUBUNTU with Internet access on, third part software and update
[/LIST]
Now the PC is updating the previous XUBUNTU 12.10 with the live CD.
Hope this could help
Nicola

---

### Post by Jilly on 2012-10-23
Hi guys , After downloading to a dvd and trying to install i am having the same problem , it shows up as an icon on the left and i can log in then nothing, i will be annoyed if i have to do another download as this was a big one. Usually it comes up with a small window immediately but not this time. Any help would be appreciated and please be aware i am a novice PC user.:(

---

### Post by muzrix on 2012-10-26
it is confirmed
before you install 12.10, make sure you have some part of clean partition beforehand. by clean i mean u should allocate some partition to either unformatted or on ext format(linux partition). use partition manager like gpart to do that

i suspect most people stuck because all their hdd partition is on existing ntfs or fat format(existing windows) and expected unity to manage the partition during installation.

---

### Post by HolyPhoenix on 2012-10-29
I have been searching for a fix to this problem, and I will test this when I get home tonight after work.

My partitions are XFS(not NTFS or FAT) which Ubuntu should be able to manage just as well as an EXT format.  This is kind of a stupid bug.  :p

---

### Post by chenzero on 2013-01-17
> **muzrix said:**
> it is confirmed
...... 
i suspect most people stuck because all their hdd partition is on existing ntfs or fat format(existing windows) and expected unity to manage the partition during installation.

Hi muzrix, I agree with you. 
I install 12.04.1 on my computer.
although the version is different, the same happened on my computer.(stopped on preparing to install, I installed 2 hard drivers, with fat32 partitions and other OS). 

it seems that took about 10 minutes to forward to next screen.

BTW, I did not check those two options on "preparing to install ubuntu" win. 
   Download updates while installing
   Install this third party software

just be patient :), HTH

---

### Post by sel1985 on 2013-01-28
In my case it was usb hard disk that was causing the problem. when i unplugged it immediately installation proceeds. "top" command might be helpful in finding your problem.

---

