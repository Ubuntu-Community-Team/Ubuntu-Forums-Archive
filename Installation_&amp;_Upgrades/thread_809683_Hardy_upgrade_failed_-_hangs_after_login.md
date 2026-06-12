---
title: "Hardy upgrade failed - hangs after login"
date: 2008-05-27
forum: Installation &amp; Upgrades
---

### Post by lightnin on 2008-05-27
Hi all

I have a P4 on an Asus board - Nvidia video.
I have 2 drives one with windows , one with ubuntu - seperate boot via bios.

I had 7.10 and the update window had been nagging that an upgrade to 8.04 was waiting and recommended.

so I clicked upgrade :(

fetched files ok - then it was installing them. I dont think it finished and then all the icons dissappeared from the desktop as if it was going to restart.  then it just hung.

so reset - and it starts ok, but hangs after I log in.

I can get in in safe mode - but then cant do alot. I cant even copy backup my home directory becuse my usb external drives are not shown.

I have a live 7.10 cd which shows the external drives, but I cant copy my home directory accross - lack of permission maybe ??

I am not fluent with the command line but am willing to give it a got step by step.

So .... where do I go from here ?

I would like to keep my programs and settings and login passwords etc to various sites

what should I do - and what should I NOT do, so I keep all my data and settings.

If I can get some help , I am hoping to get this sorted tonight - even if its an all night job !

Thanks

---

### Post by EXCiD3 on 2008-05-27
Have you tried logging in with a different Session like Gnome Failsafe? Just try the different options on the regular login screen under Session, that will be a good start.

As a warning, dont go with upgrading...it usually NEVER ends well. Sounds tempting at how easy it should be, but you can almost guarantee something breaks. Next time, create a separate /home partition and do a fresh install every time so you dont have to worry about fixing problems every time. ;)

Let me know how that goes and then we can go from there.

---

### Post by lightnin on 2008-05-27
Hi - 
sorry - had to nip out to collect my daughter. I'm here for the night now - one way or another.

I can get in with failsafe , but as I said, I cant do alot with it.  not even an internet connection.  I can see all my files and stuff - just nowhere to copy them because the external drives dont show.

I have been reading a few threads , and yes , NEXT TIME ! I will have my home somwhere seperate and install rather than upgrade - I knew when I clicked it, it was going to be trouble :cry:

---

### Post by EXCiD3 on 2008-05-27
Well, think of it this way, it can be a way for you to get started with terminal :D

So what format is your external drive? We can mount those and then you can copy your files to that and you can do a fresh install if you like, since i've got no clue as to what would cause it to freeze right away after login or how to fix it. :( but i can easily show you how to backup your data and get started with a fresh install.

---

### Post by lightnin on 2008-05-27
cant remember - but they are linux.  Yes - if I could remember how to see what they are called and mount them then I could copy over and I have the 7.10 live CD so I could at least get back to that for now.

I can see I will have to go between live cd to get on this forum and normal boot to try things, so there will be a delay for me to post answers.

... hang on a minute ...


one external is vfat - I think the other is unformatted as I messed that up when I installed 7.10

I do not have permission to copy my home directory whilst I'm on the live cd

---

### Post by markbuntu on 2008-05-27
open a terminal and type sudo nautilus. This will open nautilus and give it all root permissions and then you can mount your external drives and copy to them. If you are not root I doubt you can even see them with nautilus. Be very careful when doing this as it will let you do ANYTHING to your files.

If they are unformatted or vfat you need to format them to the format you are using first if you want to copy your home folder to them or the files will get all screwed up.

---

### Post by EXCiD3 on 2008-05-27
You can do everything from the live cd with no problems. You can mount the external drive from the live cd and your local installation with the "mount" command in terminal. 

```
mount -t vfat /dev/sdb1 /mnt/sdb1
```This command tells the system to mount the drive located at /dev/sdb1 to the folder /mnt/sdb1 format type vfat.

To find your drives just run "sudo fdisk -l" in terminal to have your drives listed.

You can change file/folder permissions with the chown command: [http://www.linuxheadquarters.com/howto/basic/chown.shtml](http://www.linuxheadquarters.com/howto/basic/chown.shtml)


Then you can go ahead and copy your files over to your external, provided you didnt run into any other problems.

---

### Post by lightnin on 2008-05-27
the vfat one I want to keep data thats on it.

The unformatted one, - I was hoping one day to get the data back by re-setting the partition table to what it was before I screwed it up - but thats another thread !

before this current problem I could copy to and from the v-fat drive

---

### Post by EXCiD3 on 2008-05-27
Is your internal drive automatically mounted? If not you can use the same mount command to mount it and then use "sudo nautilus" to browse and copy ANY files folders regardless of permissions.

---

### Post by lightnin on 2008-05-27
EXCiD3

bear with me - I am trying to figure out how to chown

I have a terminal open. trying to see all my mounted drives that I can see in gnome - cant find them yet !

then I can find the home directory?folder? that I want to chown and back up

---

### Post by lightnin on 2008-05-27
got this far.... (dont know how to put it in a box like the others do !


ubuntu@ubuntu:/$ mount
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
/dev/sdc1 on /media/Elements type vfat (rw,nosuid,nodev,shortname=mixed,uid=999,utf8,umask=077,usefree)
/dev/sdb4 on /media/disk type ext3 (rw,nosuid,nodev)
/dev/sda1 on /media/disk-1 type ext3 (rw,nosuid,nodev)
ubuntu@ubuntu:/$ 


elements is my ext drive I can recognise that :)

---

### Post by lightnin on 2008-05-27
getting closer - found the home directory :)

---

### Post by EXCiD3 on 2008-05-27
Sorry was eating dinner :)

If you have found the home directory from your installed Ubuntu you should be able to chown it or use sudo nautilus. I cant remember the default username on the livecd, however just add that into the chown command on the home directory and you should be good to go.

---

### Post by lightnin on 2008-05-27
using nautilus I got this error

Error "Invalid parameters" while copying "/media/disk...erbird.xml".

I will try the terminal and chown now

---

### Post by lightnin on 2008-05-27
I'm on Pizza and beer :)  hope you enjoyed your dinner

in the terminal I got this

ubuntu@ubuntu:/media/disk-1$ chown ubuntu home
chown: changing ownership of `home': Operation not permitted


is ubuntu the correct user for the livecd ? how do i check ?



I do realize how rubbish I am at this !  and to think I used to have my own computer shop :lolflag:  it was all MS tho - this is all weird to me !

---

### Post by lightnin on 2008-05-27
a bit more info .... I could copy a jpg file from my home directory , so it must be just some files that I dont have permission for , not all of them

---

### Post by lightnin on 2008-05-27
ok - more info...

I found nautilus had made a log file

lots of this ....

===== BEGIN MILESTONES =====
0x8177880 2008/02/26 01:01:09.8448 (USER): debug log dumped due to signal 11
0x8177880 2008/02/26 01:01:09.8454 (USER): debug log dumped due to signal 11
0x8177880 2008/02/26 01:01:09.8460 (USER): debug log dumped due to signal 11
0x8177880 2008/02/26 01:01:09.8465 (USER): debug log dumped due to signal 11

<snip>


and so on

---

### Post by EXCiD3 on 2008-05-27
Use tab to autocomplete the file/folder you are typing into terminal. I think the problem with the chown command was that the folder should look like home/ or /home. And since you were able to copy a jpg it might be a system created file meaning the ownership would probably be root. And yes it does look like the username for the LiveCD is ubuntu.

---

### Post by lightnin on 2008-05-28
sorry about that ... lost my PC (long story)

anywho, chown didnt work ... sudo chown did

copy in nautilus still didn't - _completely_

some files I got the error message, but if I pressed 'skip file' it would carry on.  of about 3800 files I had to skip maybe a dozen until I lost my PC.

ok some explination required.  Every 6 months or so my PC clogs up with dust and overheats.  I think last time I cleaned it, the CPU cooler didnt seat properly as it was running hotter than usual. Last night it overheated and wouldn't reboot so I stripped it. popped what I thought was the release lever for the graphics card (I wasn't looking - just feeling) and I popped off a capacitor that was just by the lever :(
So - today I am ruinning on a crappy PCI VGA card that I have in the attic.

another issue - one of the files that was trying to copy got stuck. I suspect a bad sector. Is there a way to check the disk and mark the sector bad ? - I cant seem to find that function ???

further down the process I am going to need to go back to a decent graphics card. Is this easy enough to do on a fully working installation or is it best to do a new install when changing hardware ?

in the mean time I will try and backup my home directory.....

---

### Post by lightnin on 2008-05-28
I have managed to get back to Gutsy with most of my settings and aps intact

Thanks both for your help !

Rich

ps - I wont mark this thread 'solved' because hardy still failed !

---

