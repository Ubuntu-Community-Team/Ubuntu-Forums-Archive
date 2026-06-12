---
title: "Ubuntu 9.10 install problems PS3"
date: 2010-02-07
forum: Installation &amp; Upgrades
---

### Post by PyrexKidd on 2010-02-07
I installed Ubuntu on my PS3.

I got a confirmation message that Ubuntu was installed and I needed to restart.

When I reboot i get a loading message and everything checks until:
```

ps3av_do_pkt: ps3av_send_cmd_pkt() failed (result=-11)
ps3av_do_pkt: failed old:10003 res:-11
EXT2-fs: ps3da1: couldn't mount because of unsupprted optional features (240).
EXT3-fs: ps3da1: couldn't mount because of unsupprted optional features (240).
EXT2-fs: ps3da1: couldn't mount because of unsupprted optional features (240).
mount: mounting non on /dev/pts failed
/init: /init: 923: KBoot loader

No default foot fs was found, or one was found and it didn't contain a message= config file.
[space between root and fs is how i see it]
If no rootfs was found, you can enter the shell here with 'sh'.  
                        Exiting will return you to this prompt.  
                        In the shell you can mount your rootfs as
/mnt/root/.

Reasons this may have happened include:

   -No drive with a rootfs was actually found
   -Your footfs does not have the correct volume lable of "/"
   -Your rootfs is corrupt (use rescue cd to fix this).

```can someone please help me.  I've been working on this project for close to a week now, and I've hit a brick wall.

Thanks in advance

---

### Post by PyrexKidd on 2010-02-07
I also tried:
```

kboot: 
/boot/vmlinux initrd=/boot/initrd.img root=/dev/sda1

```which returned:

EXT2-fs: ps3da1: couldn't mount because of unsupprted optional features (240).
EXT3-fs: ps3da1: couldn't mount because of unsupprted optional features (240).
EXT2-fs: ps3da1: couldn't mount because of unsupprted optional features (240).
mount: mounting /dev/ps3da1 on /mnt/root failed

then i went into the 'sh' and entered:
```

sudo sed -e 's/sdd1/sda1/' -i /etc/kboot.conf

```

which just gave me a
>_

those are both from the ubuntu documentation.

---

### Post by PyrexKidd on 2010-02-07
So I installed petabootloader and my ps3 will load ubuntu now but it won't connect to my wifi accesspoint. 

I can see the SSID under the network options but the ps3 won't connect.  Any help PLEASE?

---

### Post by Alec006 on 2010-02-11
I got the same problem as you.
and I don't know how to install petabootloader can you give me some help please!!

I apreciate any help thanks for your time.

---

### Post by whiteman on 2010-02-11
Maybe I did something wrong, but I chose to upgrade to 9.10 from 9.04. It installed fine, but it looks like a totally different OS. I dont know how to use it. It seems to be based on Konqueror and not Nautilus and Gnome.(I know Im showing my ignorance prbably) But I had to get rid of it. Now Im afraid to use any of the upgrades when they come out. I dont wana lose the familiar. And I always thought I was fairly quick. I went from Windowz to Mac..no problems. I used Linux in half a dozen flavs and only one..was really user friendly. I have used Redhat, Mandrake.and several others and had really given up on Linux until Ubuntu  8.04(I think) came out. I did the 9.04 upgrade and it seemed about the same.(I was hoping for a better webcam and itunes help. No change. But all that aside...I am staying with 9.04 little longer.

---

### Post by PyrexKidd on 2010-02-11
pm me and i'll e-mail you the boot loader. it's about 3.3 MB, I'll see if i can find a link for it.  or you can e-mail me here [EMAIL="pyrexxkidd@gmail.com"]pyrexxkidd@gmail.com[/EMAIL], this a catchall address so put something like UBUNTU FORUMS or PETA BOOT LOADER in the subject.  don't forget the double x.

ok so i'm an idiot.  it's not PETA boot loader. it's PETIT boot loader.  called PETITBOOT.  you can download it at the link below.
[http://linux.softpedia.com/get/System/Boot/Petitboot-34400.shtml](http://linux.softpedia.com/get/System/Boot/Petitboot-34400.shtml)

instructions to install it are below.

Extract the file to the home directory of your flash drive or extract it and burn the files to
CD in the below order.

This is an archive that should follow path

PS3 --> otheros --> otheros.bld   #Case Sensitive!

Either extract the archive to a USB drive or burn it to a cd.
It's all of 3.3 MB so I think it's better to use a usb drive

Verify the two folders with the .bld file are in the home directory
of the flash drive.

1.)Boot the PS3 in to XMB.  
   If you are having trouble with this: 
    --turn the system off  (if your stuck at kboot this may take holding the power button for 10 secconds, 
        the PS3 will beep at 5 sec, and turn off at 10sec.)
    --Hold the power button for 5 sec, this will return you back to XMB
      --if you continue holding the power button for 10 sec, it will give you another screen, choose REBOOT SYSTEM,
            this is NOT the same as restore system defaults<<--THIS WILL DELETE ALL OF YOUR SAVE DATA!

2.)Plugin USB drive, or CD.

3.)Go to:  System --> System Settings --> Install Other OS.
   This will only reinstall the boot loader and won't actually reinstall Linux.

4.)Go to:  System --> System Settings --> Primary OS --> Other OS

Welcome to Ubuntu on the PS3.  Be paitent!!!  the PS3 has next to no ram, so give it time.

---

### Post by PyrexKidd on 2010-02-11
> **whiteman said:**
> Maybe I did something wrong, but I chose to upgrade to 9.10 from 9.04. It installed fine, but it looks like a totally different OS. I dont know how to use it. It seems to be based on Konqueror and not Nautilus and Gnome.(I know Im showing my ignorance prbably) But I had to get rid of it. Now Im afraid to use any of the upgrades when they come out. I dont wana lose the familiar. And I always thought I was fairly quick. I went from Windowz to Mac..no problems. I used Linux in half a dozen flavs and only one..was really user friendly. I have used Redhat, Mandrake.and several others and had really given up on Linux until Ubuntu  8.04(I think) came out. I did the 9.04 upgrade and it seemed about the same.(I was hoping for a better webcam and itunes help. No change. But all that aside...I am staying with 9.04 little longer.


of from what i can tell there were some issues upgrading 9.4 to 9.10.  a cleen install is recommended.
[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)
[http://ubuntuforums.org/showthread.php?t=1346288](http://ubuntuforums.org/showthread.php?t=1346288)

i included a screen shot of 9.10.  it's definitely a gnome desktop.
I'll do what I can to help you out

---

### Post by Alec006 on 2010-02-12
first of all thanks for your time!!

I did what you said but now i'm stuck in the boot screen where you can choose screen resolution from 720p 1080 blabla or booting from os game i got there but the screen is empty and i dunno how booting ubunto thanks pal!!

---

### Post by Alec006 on 2010-02-15
> **Alec006 said:**
> first of all thanks for your time!!

I did what you said but now i'm stuck in the boot screen where you can choose screen resolution from 720p 1080 blabla or booting from os game i got there but the screen is empty and i dunno how booting ubunto thanks pal!!



do I install first lpettit loader or I should install the os first?

I installed the os first and it doesn't work.

thanks!!

---

### Post by PyrexKidd on 2010-03-31
you have to install the OS first and then boot back into the PS3 operating system and install the boot loader form the system --> settings --> install boot loader.  (take the install disk out of the PS3 to be sure it grabs the boot loader off your USB drive.)  then you can select boot from other OS.

Let me know if this works.  I know it's been a month.

---

### Post by vivaporu on 2010-04-12
hey maybe you can help me i am in the same boat alec 0006 is in 
skyblue ubuntu background with keys:0=safe 1=720p .....del=GameOS
so not sure what went wrong or where do i go from here. dont want to update to the killer 3.21 otheros killer without giving linux on ps3 a try regret for putting off for so long ,thanks in advanced

---

### Post by drreed on 2010-04-13
Last week PS3's got an update from online that nixed any chance of installing an alternate OS. Other OS isn't an option on the box after that upgrade. You can refuse it, but you won't be able to play on their online games network.

It was april 1st, no fooling!


[http://hackaday.com/2010/03/31/sony-removes-ps3-linux-support-with-an-update-errrrr-downgrade/](http://hackaday.com/2010/03/31/sony-removes-ps3-linux-support-with-an-update-errrrr-downgrade/)

---

### Post by PyrexKidd on 2010-04-13
> **drreed said:**
> Last week PS3's got an update from online that nixed any chance of installing an alternate OS. Other OS isn't an option on the box after that upgrade. You can refuse it, but you won't be able to play on their online games network.

It was april 1st, no fooling!


[http://hackaday.com/2010/03/31/sony-removes-ps3-linux-support-with-an-update-errrrr-downgrade/](http://hackaday.com/2010/03/31/sony-removes-ps3-linux-support-with-an-update-errrrr-downgrade/)

there is a way around it.  Google "ps3 proxy hack" and check out [http://geohotps3.blogspot.com/](http://geohotps3.blogspot.com/)

DISCLAIMER:
THIS POST IS INTENDED FOR __EDUCATIONAL__ PURPOSES __ONLY__ AND DOES NOT IN ANY WAY CONDONE, ENCOURAGE, OR PROMOTE HACKING, TWEAKING, OR USING THE PS3 IN ANY MANNER OTHER THAN EXPRESSLY STATED IN THE ELUA.  HACKING IS ILLEGAL.  DON'T BRAKE THE LAW JUST TO PLAY SOME GAMES.

---

### Post by drreed on 2010-04-13
> **PyrexKidd said:**
> there is a way around it.  Google "ps3 proxy hack" and check out [http://geohotps3.blogspot.com/](http://geohotps3.blogspot.com/)

DISCLAIMER:
THIS POST IS INTENDED FOR __EDUCATIONAL__ PURPOSES __ONLY__ AND DOES NOT IN ANY WAY CONDONE, ENCOURAGE, OR PROMOTE HACKING, TWEAKING, OR USING THE PS3 IN ANY MANNER OTHER THAN EXPRESSLY STATED IN THE ELUA.  HACKING IS ILLEGAL.  DON'T BRAKE THE LAW JUST TO PLAY SOME GAMES.


LOL that didn't take long!  It's only been 13 days since that announcement. :guitar:

I checked out that article, and I wouldn't even call that a proof of concept. He's working on it, along with a few thousand other people! It remains to be seen what will come of that.  I'm more interested in the ps3 for reasons other than games, but I'd be afraid to brick the unit attempting such a thing. Maybe I can find a used one to experiment on? After Arduino . . .

---

### Post by PyrexKidd on 2010-04-14
> 
hey maybe you can help me i am in the same boat alec 0006 is in 
skyblue ubuntu background with keys:0=safe 1=720p .....del=GameOS
so not sure what went wrong or where do i go from here. dont want to  update to the killer 3.21 otheros killer without giving linux on ps3 a  try regret for putting off for so long ,thanks in advanced
what version of ubuntu are you installing?
did you download and install petitboot?
what error message or screen are you getting stuck at exactly?

the petit boot loader can be found here:
[http://linux.softpedia.com/get/Syste...ot-34400.shtml]("http://linux.softpedia.com/get/System/Boot/Petitboot-34400.shtml")

---

### Post by vivaporu on 2010-04-14
> **PyrexKidd said:**
> what version of ubuntu are you installing?
did you download and install petitboot?
what error message or screen are you getting stuck at exactly?

the petit boot loader can be found here:
[http://linux.softpedia.com/get/Syste...ot-34400.shtml]("http://linux.softpedia.com/get/System/Boot/Petitboot-34400.shtml")

Ubuntu 9.10 alternative ppc + ps3 ,then reinstalled petitboot from good sources ,i don't get actual error just a normal looking sky blue background and terminal type text in the bottom left saying
0=safe 1=720p 2=1080i 3=1080p del=GameOS,i can choose any of those setting which changes the resolution on the screen but thats it , i left it in that state for an hour before rebooting , 
really wanted to make it work but about to give up and update unless geohot post his hacked custom update plus not sure how to do proxy hack tried looking that up to ,but failed .....damn fail bus keeping getting on it

---

### Post by PyrexKidd on 2010-04-15
> **vivaporu said:**
> Ubuntu 9.10 alternative ppc + ps3 ,then reinstalled petitboot from good sources ,i don't get actual error just a normal looking sky blue background and terminal type text in the bottom left saying
0=safe 1=720p 2=1080i 3=1080p del=GameOS,i can choose any of those setting which changes the resolution on the screen but thats it , i left it in that state for an hour before rebooting , 
really wanted to make it work but about to give up and update unless geohot post his hacked custom update plus not sure how to do proxy hack tried looking that up to ,but failed .....damn fail bus keeping getting on it


i work tech support I totally understand the fail bus.  bear with me.  I'll take a deeper look into this when I get home from work.

what happens when you choose GameOS?  it sounds like you might have a bad install of Ubuntu.  it does take the ps3 a minute to load since it only has 512mb of ram.

---

