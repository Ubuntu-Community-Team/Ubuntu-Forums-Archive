---
title: "Installing to a 2GB SSD"
date: 2011-05-25
forum: Installation &amp; Upgrades
---

### Post by underquark on 2011-05-25
I realise that this might be a bit of a niche market question but with lots of ex-corporate "thin clients" for sale very cheaply it might interest a few of you if this can be made to work.
 
I have a Hewlett Packard t5730 with 1GB RAM and a 160GB PATA HDD runing very well. I have got my hands on some other machines (some with Solid-State "Discs", some with RAM and some without) and have put together a HP t5730 with 1GB RAM and 2GB SSD.
 
I could just stick a hard drive in it but I would like to make a completely silent machine if possible. Also, if the machine is stood on its side the hard drive gets noisier and I worry about damaging the drive. A disc-less machine can take up less desk space and can even be attached under the desk so long as ventilation is adequate.
 
How could I go about installing vital files to the SSD to boot the device whilst hiving off other files or partitions to removalbe media? I've tried running 10.04 off a Live "CD" on USB stick and the speed of the machine is fine. My needs are browsing (Firefox, including Flash support to watch YouTube videos), editing small documents (saving to .DOC or .RTF format), creating simple presenations (with still images and no fancy effects).
 
Here's what I have:
HP t5730 machine with 1.5MHz Celeron CPU
1GB RAM (maximum it will take)
2GB SSD (or DOM; I don't care if the Windows it contains gets trashed)
Two 4GB USB sticks that I intend to leave installed inside the machine
A 1GB USB stick to use as a Live "CD"
Internet access
Possibility of storage on local network (for images and other large files).
 
If anyone has done this already then I'd appreciate their input. Thanks.

---

### Post by Joe of loath on 2011-05-25
Run Ubuntu persistently from the internal SSD, using a USB stick as the persistent storage.

---

### Post by underquark on 2011-05-26
Thanks. Yes, I can see that as one solution but I had thought to try and have boot, vital (or, at any rate, most likely to be needed quickly) system files and swap on the SSD (100MB, 900MB, 1GB or something) and maybe try and get /usr, /var and others on one 4GB stick and /home onto the other 4GB stick.  Or would it be better to retain one 4GB stick purely for data?

I remember reading on a Debian forum that one user's view of an ideal system would be to have a small SDD for boot and two large storage drives - he was planning on using 200GB hard drives but my needs are more modest. Basically, is there a "best" way to, say, plug in two blank 4GB sticks and then boot from a Live 1GB stick and then set up all the various partitions at this stage?

Maybe instead of trying to shoehorn in the full ubuntu and delete the stuff I don't need I should d a minimal install and then add in the stuff that I do need.

---

### Post by kerry_s on 2011-05-26
yeah, a base install & then apt-get what you need would be the best.
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by underquark on 2011-05-28
Well, thanks for the input.  I'm going to try the following and I'll see how I get on:

Partition the 2GB SSD thus:
1 /boot 50MB
2 /tmp 750MB
3 /lib 400MB
4 /home 800MB

1 I note that 30+ gets taken up on a lot of desktop systems so this should be adequate for one OS.
2 I looked at a few systems and many had 680MB or so in use)
3 Bit of a guess, really.
4 I thought of putting /home elsewhere but it contains a lot of settings and stuff in hidden files.  Once you strip out the Documents, Downloads and porn from some users /home directory or partition then 800MB seems plenty.

/var and /usr are big storage users so I may put them on a USB stick thus:
/var 1000MB
/usr 3000MB

I'll need to ensure that Documents is directed to the other 4GB stick, Downloads also and that the Desktop is kept clear.  /var could probably do with a periodic spring clean but I don't anticipate frequent new package downloads and updates will be done manually from time to time.

I don't have any swap set up.  I'll see how it goes and consider a swapfile on USB if I really need it.  Booting from the Live USB and running Firefox and watching a YouTube video, for instance, uses only 325MB. Still plenty of space to edit the size of documents that this machine will be being used for and have RAM left over.  Obviously, hibernation won't be possible but better to properly save everything at end of day anyway, I'd say.

---

### Post by kerry_s on 2011-05-28
> **underquark said:**
> Well, thanks for the input.  I'm going to try the following and I'll see how I get on:

Partition the 2GB SSD thus:
1 /boot 50MB
2 /tmp 750MB
3 /lib 400MB
4 /home 800MB

1 I note that 30+ gets taken up on a lot of desktop systems so this should be adequate for one OS.
2 I looked at a few systems and many had 680MB or so in use)
3 Bit of a guess, really.
4 I thought of putting /home elsewhere but it contains a lot of settings and stuff in hidden files.  Once you strip out the Documents, Downloads and porn from some users /home directory or partition then 800MB seems plenty.

/var and /usr are big storage users so I may put them on a USB stick thus:
/var 1000MB
/usr 3000MB

I'll need to ensure that Documents is directed to the other 4GB stick, Downloads also and that the Desktop is kept clear.  /var could probably do with a periodic spring clean but I don't anticipate frequent new package downloads and updates will be done manually from time to time.

I don't have any swap set up.  I'll see how it goes and consider a swapfile on USB if I really need it.  Booting from the Live USB and running Firefox and watching a YouTube video, for instance, uses only 325MB. Still plenty of space to edit the size of documents that this machine will be being used for and have RAM left over.  Obviously, hibernation won't be possible but better to properly save everything at end of day anyway, I'd say.


i would go with just 1 / partition, confining is only going to cause problems down the line, plus you waste space thats not used. with 1 partition it can shrink & grow, much better use of space.

---

### Post by underquark on 2011-05-28
Yes, I'm getting carried away with partitioning.  I went for one / on the SSD and tried an install but accidentally installed the full 10.04 rather than the minimal.

For some reason my Startup Disk Creator doesn't let you select different iso (or, rather it lets you think you are selecting a different iso but then  reverts to the one you used previously which, in my case, was the full install of 10.04 32-bit that I'd used to install on another PC).  Anyway that's a different problem.

To cut a long story short, the full 10.04 seems to install but takes a very long time.  Unfortunately when I reboot I get the ubuntu splash screen wither 'forever' or at least for far longer than I care to accept.  Still, quick enough to reboot with Live USB and get the machine going again.  Son now playing with it so will try again later with the minimal install (used a differnet machine to make the startup USB whilst I find out what is wrong with Startup Disk Creator on my main machine).

---

### Post by underquark on 2011-05-28
Tried the minimal install, command-line interface.  It's a bit slow - I had always been meaning to read "The Grapes of Wrath" by John Steinbeck and managed to get to page 62 despite a break for dinner.  After all that the best I can get it to do after re-booting is a "grub rescue" prompt.  ls shows a number of plausible discs/partitions so there's likely a way to get into it but I think I'll leave to for tonight.

Answers to anticipated questions:
Have I set the SSD as a Primary partition? - Y
Have I set the SSD as bootable - Y
What does df show? - it doesn't as df isn't a recognised command from grub-rescue. (And nor are grub-update, sudo, apr-get etc.).

So, back in with the Live USB, re-boot (remembering to hit <F10> to select USB as boot-first device) and I re-set the background, change the minimize, maximize buttons over to their correct side again and re-install Flash and it's business as usual but I'd still like to crack this.

---

### Post by kerry_s on 2011-05-28
mini install is cli, there is no gui. your suppose to apt-get what you want.

you should try lubuntu instead, should be lighter & faster.
[http://lubuntu.net/](http://lubuntu.net/)

sounds like your ssd is 1 of those slower 1's.

---

### Post by underquark on 2011-05-29
Yes, I had intended:

```
sudo apt-get update
sudo apt-get install xorg xterm gdm lxde menu epiphany gksu synaptic --no-install-recommends
sudo service gdm start
```

but am stuck at grub-rescue.  Having re-booted with the Live USB I can see that all the files appear to be on the SSD but Grub is presumably not pointing there at boot time.  I remembered to set the SSD as first boot device, I've tried update-grub from within the Live booting but it just reports that it can't find / and am I sure that /dev is present.

Maybe it is just a very slow SSD.  I'll see if I can fix the Grub problem and then maybe give lubuntu a whirl.

---

### Post by kerry_s on 2011-05-29
2gb is so tight, i'm thinking puppy would be the best choice, it's like 128mb & you have more than enough ram that it can run from there.

[http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm](http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm)

---

### Post by underquark on 2011-05-29
I had actually tried puppy (lupu 5.02) on my main computer but couldn't get it to boot on the HP but, yes, I agree that puppy looks very good - I'll maybe give it a go on a 1GB/1GB machine that I have got as I want to set up a small machine to connect to my PVR (Topfield TF5800) and to attach some storage to.

I booted from a Live USB of 10.04, managed to get grub pointing at the SSD, booted it, read a few more pages of TGofW whilst it downloaded and installed the packages and it has re-booted into the LXDE desktop successfully.

In case I need to boot into the Live USB again I've created a 4GB stick version and left it attached inside the HP.  If all continues to work well then that becomes the main place for documents, downloads, music etc.

So, thanks all and seems to be working.

---

### Post by underquark on 2011-05-30
I guess I should marked this as "Solved".  There is, of course, more than one answer but what I have done is working satisfactorily for me.

In summary:
Running ubuntu on a HP t5730 with 2GB SDD and 1GB RAM
(also likely applicable to other ex "thin clients").

Requirements:
1GB USB drive
Two 4GB USB memory sticks (or larger)
Internet connection

Method:
Download the Minimal Install iso of the Live CD (I used ubuntu 10.04)
Use UNetbootin or other method to make the 1GB USB drive into a bootable alternative to CD

Remove the side panel of the HP and ensure all USB sticks removed
Insert 1GB Live USB into a front USB socket
Switch on the machine
Press [F10] to get into the BIOS, down-arrow to third line (Advanced CMOS) and select USB as the first boot device.
Press [F10] and [Enter] (save and exit BIOS)

Once the Live session has statred, insert the two 4GB USB sticks into the internal sockets
Now choose to Install ubuntu from the Command Line Prompt
Choose to use the whole disk and erase any existing operating system
Choose to manually partition the drives
Create a primary partition on the SSD, formatted Ext4, bootable, mount point / (root)
Partition the first 4GB USB stick as extended and create a 1GB partition, Ext4, mount point /var and create a 3GB partition, Ext4, mount point /usr.
Partition the second USB stick as one extended partition, Ext4

- I chose to leave /home on the SSD and only to store data to the second USB stick but some might argue for mounting the second USB stick as /home.

When you proceed with the installation it will take a considerable time as many packages have to be downloaded, unpacked, installed.

Eventually you can reboot.
Press [F10] to get into BIOS and select ATA as boot device

You should now be at the command line of your new ubuntu system.  To get a graphical interface, web browser etc. I issued the following commands:

sudo apt-get update
sudo apt-get install xorg xterm gdm lxde menu firefox gksu synaptic --no-install-recommends
sudo service gdm start

You can choose a different browser, xfce instead of lxde etc.

---

