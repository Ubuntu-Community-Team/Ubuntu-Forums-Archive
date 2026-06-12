---
title: "need help downloading 9.10"
date: 2010-01-15
forum: Installation &amp; Upgrades
---

### Post by michelleishell on 2010-01-15
I have the demo, or desktop version of ubuntu on a flashdrive, and when I click the "install 9.10" icon on the desktop, a window pops up that says "application problem: sorry, the program 'ubiquity' has closed unexpectedly". I'm a total beginner on this, i've tried downloading the "server" version of ubuntu but when I tried to open it, it also "closed unexpectedly". Any help? Thanks !

---

### Post by michelleishell on 2010-01-15
now the update manager says "E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

---

### Post by Techsnap on 2010-01-15
Can you not download and install Ubuntu using a CD from [http://www.ubuntu.com](http://www.ubuntu.com) not quite sure what you mean but it sounds like you have a bad install image.

---

### Post by alwayshere on 2010-01-15
If you are new to linux you are best to use a LTS version of ubuntu which is stable.

I use ubuntu LTS 8.04 found here [http://releases.ubuntu.com/8.04/]("http://releases.ubuntu.com/8.04/")
all the help and info for it you will need can be found here [https://help.ubuntu.com/8.04/index.html]("https://help.ubuntu.com/8.04/index.html")


 ***Please Note*** if you are going to install this on a pc that already has an o.s look into "virtual box" first see all about it here [http://www.virtualbox.org/]("http://www.virtualbox.org/")

---

### Post by michelleishell on 2010-01-15
thanks, i'll try LTS :]

---

### Post by michelleishell on 2010-01-15
it says it's a server install CD, do I need to burn it to a CD and then put it in my computer, or can I just download it and open it?

---

### Post by audiomick on 2010-01-15
Hallo.
I you really want to build a server, that would be right.

Bear in mind that the server edition has no graphical desktop, i.e. you have to do everything with the command line. You don't really sound like someone who wants that...:)

I would suggest that you, before you go any further, read through this,
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

and pay particular attention to the link about the MD5Sum. I suspect that the CD you used for your first attempt was corrupt.

Also, you should run the "CD check" option in the menu when you boot from the cd.

---

### Post by alwayshere on 2010-01-15
You do notwant to download the server version you should download the PC (Intel x86) desktop CD .Which is an iso file which you will need to burn to a cd or dvd then use that cd or dvd to install ubuntu 8.04

here is a direct link to that iso download 

[http://releases.ubuntu.com/hardy/ubuntu-8.04.3-desktop-i386.iso]("http://releases.ubuntu.com/hardy/ubuntu-8.04.3-desktop-i386.iso")

---

### Post by michelleishell on 2010-01-15
thanks so much! I did read the page about burning an iso, and the MD5SUMS before I tried to burn a CD of ubuntu the first time, but I had no idea what a terminal was (figured it out later, and felt stupid) so I skipped that part haha

---

### Post by alwayshere on 2010-01-15
lol I have been there, just sing out if ya need more help the only stupid question is one thats not asked .

---

### Post by michelleishell on 2010-01-15
Hmm, the links at [http://releases.ubuntu.com/hardy/](http://releases.ubuntu.com/hardy/) of MD5SUMS just go to sites with weird codes on them, "371bd54267de6169a602bd1fafa2abfd *ubuntu-8.04.3-alternate-amd64.iso" how do I actually download them ?

---

### Post by Kafubie on 2010-01-15
> **michelleishell said:**
> I have the demo, or desktop version of ubuntu on a flashdrive, and when I click the "install 9.10" icon on the desktop, a window pops up that says "application problem: sorry, the program 'ubiquity' has closed unexpectedly". I'm a total beginner on this, i've tried downloading the "server" version of ubuntu but when I tried to open it, it also "closed unexpectedly". Any help? Thanks !

Well, I Downloaded unetbootin. Google search it.
Used that, but to to actually use the bootable usb.  You have to restart your system, than go to BIOS or anything that's relevant to booting.

---

### Post by alwayshere on 2010-01-15
here is the direck link to the 8.04 lts iso download that i posted earlier ya must have mist it 

[http://releases.ubuntu.com/8.04/ubun...sktop-i386.iso]("http://releases.ubuntu.com/8.04/ubun...sktop-i386.iso")

---

### Post by michelleishell on 2010-01-15
oh I did download the 8.04, but to burn it to a CD it was recommended to download an MD5SUM to the same directory as the iso to verify it

---

### Post by alwayshere on 2010-01-15
just burn the iso to a cd or dvd thats all i ever do

MD5SUM ?? must be some kind of supernerd stuff i just an average joe 

if it works its good if it ant broke i dont fix it

---

### Post by michelleishell on 2010-01-15
alright!

---

### Post by chillyomi on 2010-01-15
i dint get it whats the problem

---

### Post by michelleishell on 2010-01-15
I burnt the CD, and nothing came up on the computer so I opened it on the computer and it had a bunch of files, and I clicked "download synaptic package", and then an error came up saying "E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
"
I put it in a terminal and it said
"dpkg: parse error, in file '/var/lib/dpkg/updates/0007' near line 0:
 field name `' must be followed by colon
"

---

### Post by alwayshere on 2010-01-15
First  does your pc alreay have another o.s on you want to keep if so use virtual box to run your ubuntu cd you have made  to install ubuntu.

if ubuntu is going top be the only o.s do the below

you do know you are ment to boot it?? eg go to your bios and set it to boot from cd first  then put cd in pc and turn it on let the cd boot up and you then install ununtu from there.

---

### Post by michelleishell on 2010-01-15
nope, it doesn't have another o.s., haha I didn't know that, i'll try it !

---

### Post by michelleishell on 2010-01-16
wow that took me waaaaay too long to figure out, haha, thanks so much for your help!

---

### Post by sliketymo on 2010-01-16
The MD5SUM is used to verify the integrity of the downloaded .iso,to make sure the download has everything it is supposed to have.You compare the md5sum of the .iso with the proper one at the previous site you visited,ie:the amd64 for the amd64.iso,x86_32 for the x86_32.It is just an extra check to help make sure you don't waste a lot of time trying to get a burned cd to install that is not complete.

---

