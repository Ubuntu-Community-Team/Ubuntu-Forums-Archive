---
title: "live cd won't mount"
date: 2010-08-28
forum: Installation &amp; Upgrades
---

### Post by salima on 2010-08-28
[http://ubuntuforums.org/showthread.php?t=1005979&highlight=block+device+%2Fdev%2Fscd0+write-protected%2C+mounting+read-only&page=2](http://ubuntuforums.org/showthread.php?t=1005979&highlight=block+device+%2Fdev%2Fscd0+write-protected%2C+mounting+read-only&page=2)

this thread had some information but i need some clarification as the results i got from the diaagnostics were not the same as the OP.

  	 	 	 	 	 	  my prooblemm is when i put the cd in the drive, i get this error:

Unable to mount Ubuntu 10.04
 DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
 
when i type this command:
  	 	 	 	 	 	  sudo mount -t iso9660 /dev/scd0 /media/cdrom
 i get this message:
  	 	 	 	 	 	  mount: block device /dev/scd0 is write-protected, mounting read-only  
 mount: /dev/scd0 already mounted or /media/cdrom busy  
 mount: according to mtab, /dev/scd0 is mounted on /media/cdrom0 



(that was a suggestion from a different thread) 



from the thread i gave the link top at the beginning of this post, here are the results of the commands i typed:


   	 	 	 	 	 	  salima@salima-desktop:~$ cat /etc/fstab 
 # /etc/fstab: static file system information. 
 # 
 # <file system> <mount point>   <type>  <options>       <dump>  <pass> 
 proc            /proc           proc    defaults        0       0 
 # /dev/sda1 
 UUID=7330d690-e97a-41ee-9143-4e81eea14f0b /               ext3    relatime,errors=remount-ro 0       1 
 # /dev/sda5 
 UUID=f175e435-0e94-42c1-be82-858396ad3083 none            swap    sw              0       0 
 /dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0 
 salima@salima-desktop:~$ mount 
 /dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro) 
 tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755) 
 /proc on /proc type proc (rw,noexec,nosuid,nodev) 
 sysfs on /sys type sysfs (rw,noexec,nosuid,nodev) 
 varrun on /var/run type tmpfs (rw,nosuid,mode=0755) 
 varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777) 
 udev on /dev type tmpfs (rw,mode=0755) 
 tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev) 
 devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620) 
 fusectl on /sys/fs/fuse/connections type fusectl (rw) 
 lrm on /lib/modules/2.6.27-17-generic/volatile type tmpfs (rw,mode=755) 
 securityfs on /sys/kernel/security type securityfs (rw) 
 binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev) 
 gvfs-fuse-daemon on /home/salima/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=salima) 
 /dev/scd0 on /media/cdrom0 type iso9660 (ro) 
 salima@salima-desktop:~$  
 
 
    	 	 	 	 	 	  salima@salima-desktop:~$ sudo mount /media/cdrom0 
 [sudo] password for salima:  
 mount: block device /dev/scd0 is write-protected, mounting read-only 
 mount: /dev/scd0 already mounted or /media/cdrom0 busy 
 mount: according to mtab, /dev/scd0 is already mounted on /media/cdrom0 



   	 	 	 	 	 	  salima@salima-desktop:~$ dmesg | tail --lines=15 
 [ 4703.283926] Buffer I/O error on device sr0, logical block 358298 
 [ 4704.262177] end_request: I/O error, dev sr0, sector 1433188 
 [ 4704.262191] Buffer I/O error on device sr0, logical block 358297 
 [ 4707.899024] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK 
 [ 4707.899037] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current]  
 [ 4707.899045] sr 0:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error 
 [ 4707.899055] end_request: I/O error, dev sr0, sector 1433192 
 [ 4707.899063] Buffer I/O error on device sr0, logical block 358298 
 [ 4711.530218] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK 
 [ 4711.530230] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current]  
 [ 4711.530239] sr 0:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error 
 [ 4711.530248] end_request: I/O error, dev sr0, sector 1433192 
 [ 4711.530256] Buffer I/O error on device sr0, logical block 358298 
 [ 4712.429421] ISO 9660 Extensions: Microsoft Joliet Level 3 
 [ 4712.475445] ISO 9660 Extensions: RRIP_1991A 
 salima@salima-desktop:~$  
 



the fellow fixed his by  adding or editing his menu.lst in grub, but since my results are not exactly the same as his i dont know what it is i should be adding or editing.


but it seems to have something to do with installing generic ide drivers and disabling the flopy drive and another item that even he didnt know what it was doing


hope someone understands this...

---

### Post by mortasa on 2010-08-28
Check your other operating systems if you are using. If you don't shutdown them properly or, if you hibernate any of other operating systems, CD or any drive can not mount for you. CD can mount only in Read only mode. Even if you hibernated your previous ubuntu, you will get this same problem. Just make sure about this and try again.

Thanks.

---

### Post by vivek40 on 2010-08-28
I believe your cd is mounted....If you are trying to mount a live cd , try using it .. I mean, try rebooting the system with the cd in and make sure to enable the system to boot from the cd drive rather than hard disk else you wont know!
(got to sleep.. will have a re look tomo)

---

### Post by salima on 2010-08-29
> **mortasa said:**
> Check your other operating systems if you are using. If you don't shutdown them properly or, if you hibernate any of other operating systems, CD or any drive can not mount for you. CD can mount only in Read only mode. Even if you hibernated your previous ubuntu, you will get this same problem. Just make sure about this and try again.

Thanks.

ubuntu 8.10 is the only operating system on my pc now and i always shut down the same way-never hibernate.


[QUOTE=Vivek} I believe your cd is mounted....If you are trying to mount a live cd , try using it .. I mean, try rebooting the system with the cd in and make sure to enable the system to boot from the cd drive rather than hard disk else you wont know!
(got to sleep.. will have a re look tomo)  	{QUOTE]

thanks Vivek-i tried starting the pc with the cd in the drive but it just booted as usual. how do i check if i have the system enabled for dual boot? i think i may have had to do this on another machine, going into the bios and changing or setting up something, but i forgot how. i havent done much with bios...

---

### Post by vivek40 on 2010-08-29
No this does not have anything to do with dual boot. you just have to go to bios and change the settings. It should be something like the first boot option should be from the cd , the second from the hard disc... You will automatically know once you enter bios.

Let me know if you are unable to figure it out

Vivek

---

### Post by salima on 2010-08-30
> **vivek40 said:**
> No this does not have anything to do with dual boot. you just have to go to bios and change the settings. It should be something like the first boot option should be from the cd , the second from the hard disc... You will automatically know once you enter bios.

Let me know if you are unable to figure it out

Vivek


hi vivek-
in   bios i changed the option to boot first from cdrom, second floppy, hitachi (my hard drive). i could not see any way to make it cdrom, hitachi and floppy. i do have a floppy drive by the way...

anyway, i tried a number of times but the pc boots without using the cd-goes slower as though it is confused about something, but then ignores the cd altogether.

i am thinking before i go any further with this and drive myself and everybody nuts i better give the cd to someone who is willing to try and boot with it to make sure it is ok. the person i had check it for me i think only displayed the contents, which had lots of colorful folders but maybe that was not enough to prove it is a good cd.  i only know one person in the city who would be savvy enough to use a live cd, though i should try asking my pc repairman just to test his competency...he is supposed to come because i also have this restart and overclocking error issue, but he has been held up i assume...


but for the time being, if you could let me know if the order to boot in the bios is ok the way i have it set now-cdrom, floppy, hard drive....now the roads are bad and i cant get out.. when i get positive verification that i have a good, live cd, if it still doesnt work i will get back to this thread...

---

### Post by varunendra on 2010-08-30
Sorry for unsolicited advise, but by the time Vivek gets back to your thread, I think you may try a few more things.

The boot order is okay, it seems to be a physical problem in reading the cd. It'll be nice to make sure that the cdrom drive is working in the first place.

So, are you sure the cdrom drive is functional? Does it read other CDs or is the problem same with all CDs?

Also, if your computer's BIOS supports booting from a USB flash drive, you may wish to try [Slax]("http://www.slax.org/get_slax.php") on USB. It is only 200MB download and easy to install on a flash drive.

---

### Post by vivek40 on 2010-08-30
[LEFT]Hi! sorry .. could not get back earlier.. as varunendra said,your boot order is right and  it should be good to check the cd drive before we go ahead with the below.
The only reason for a system which is configured to boot from a cd , to totally ignore a cd and to boot from the hard disk could be that the cd is not burnt properly.
It would be good if you could just do a md5sum test on the cd.. I had a similar problem with a Mint CD recently... do the below things one by one:-

1. first you will have to check the md5hash of the iso image that you would have downloaded...(based on what image you have downloaded you can get the md5 hash from here..[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)).. so go to the terminal , cd to the directory where you have your iso image saved and just type this :-

[HTML]md5sum myisoimage.iso [/HTML]and verify if the iso image downloaded has the same hash as in the table on the link above.NOTE-PLEASE CHANGE "MYISOIMAGE.ISO" TO THE NAME OF YOUR ISO IMAGE FILE. 

2. now check the md5 of the cd . It is quite possible that the cd is not burnt properly.So after placing the cd in the drive .. go to the terminal, cd to your home directory and give this command:-

[HTML]md5sum /dev/cdrom[/HTML]3. just match the md5 sums .. they are supposed to be the same.

(NB:Would be good if you could  post the commands you gave and the output)
[/LEFT]

---

### Post by varunendra on 2010-08-31
Vivek,
Is it possible to check the md5sum of a physical CD even if it is not properly readable? Because she mentioned that someone checked it for her showing its contents:
> **salima said:**
> ..the person i had check it for me i think only displayed the contents, which had lots of colorful folders..
..while she is unable to see the same contents on her computer. So I guess either the drive is malfunctioning or there may be a problem with the OS. In either case I doubt the md5sum value of the cd can be determined.

Also, I doubt she has its downloaded iso (ref. to same quote above). To me, it seems she has directly got the physical cd from the person.

However, I'm not sure about these, so would like to know how it goes. Personally, what I do in such cases is to simply disconnect the hard disk and let the PC boot with the cd alone. In case it fails, I replace the cd with a trusted one. If it succeeds- means (mostly) the previous cd was defective, if it fails too- means the drive is defective. With same approach in mind, I asked if she is able to read other CDs.

---

### Post by vivek40 on 2010-08-31
True varun!.. that is why i asked the OP to check the cd drive before doing any of these, as you had suggested. Moreover if the cd is not burnt properly, most of the time you would get some sort of IO error as a result of md5sum check. 
and that is another reason I asked her to post back the output. As far as she having the ISO image with her is concerned, I seriously dont know.Anyway if she has then she could just check that too.... 
Vivek!

---

### Post by salima on 2010-08-31
hi guys-
thanks a lot...

i think also it would be good to check the cd drive...i can read data disks, i can play commercial cd's,  i can play the copies someone made for me on cd-r disks. i dont have any other kind of disks to try...

here is something i got about my cdrom from lshw:
  	 	 	 	 	 	    *-cdrom  
                 description: DVD-RAM writer  
                 product: BAER DH-20A4P  
                 vendor: MOSER  
                 physical id: 0.0.0  
                 bus info: scsi@0:0.0.0  
                 logical name: /dev/cdrom  
                 logical name: /dev/cdrw 
                 logical name: /dev/dvd  
                 logical name: /dev/dvdrw  
                 logical name: /dev/scd0 
                 logical name: /dev/sr0  
                 version: 9M74  
                 capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram  
                 configuration: ansiversion=5 status=nodisc 



and about the image: 

i burned it myself, took me four nights so it had to be paused and resumed, but the brasero burner said it was ok. when i created the disk with brasero it told me the disk was created successfully. i do realize both of these can still be bad, but just letting you know what i know.



 now the iso image is stored in a folder on my desktop-and i notice it has a lock on it, this has been happening to so many files and i dont know if it should be happening or not. when i click on properties on the image it says it is 'read-only'...is it supposed to be read only?

i will go on too checking the md5 hash next and see what happens...

---

### Post by salima on 2010-08-31
**md5 Hash**
 d044a2a0c8103fc3e5b7e18b0f7de1c8  
 **Version**
 ubuntu-10.04-desktop-i386.iso
 



the directory to my file goes like this:

 /home/salima/Desktop/desktop folders/10.04 install disk
 and the file name is:
 ubuntu-10.04-desktop-i386.iso
 

 i think by default when i open a terminal i am automatically in the home directory...

so for the above i typed:
 md5sum ubuntu-10.04-desktop-i386.iso 

 here is what happened:

 salima@salima-desktop:~$ md5sum ubuntu-10.04-desktop-i386.iso 
 md5sum: ubuntu-10.04-desktop-i386.iso: No such file or directory 
 salima@salima-desktop:~$  
 

 it is telling me the file does not exist? But there it is...though it is locked and readonly...

---

### Post by salima on 2010-08-31
oops-
check the md5 of the cd cant happen...i gather i needed the first command to work to have something to check the cd against...

also, to answer varun...i only saw three options for boot, so i dont think i would be able to boot from a usb stick. however, i did create one from the program under System, Admin, Create a USB Startup Stick

i do not understand where the original iso image went...by the way, the one i have now was created from the cd itself...i think. i have been working on this now for a long time. so if there is a problem with the cd, i would have made a bad iso copy anyway.

somehow the original copy got lost. 

if i can reach this person in town he would be able to check the cd for real...he installed 8.10 with the same disk i used to put 8.10 on this machine and he has some interest in it all. so i know he knows how to install from a disk...why i dont remember having to change the boot options at that time is beyond me...but i do tend to get mixed up, which is why i try to write everything down.

maybe the best thing to do is start a new download of the image so that i am doing something in the meantime, then try and get that fellow to check out my cd. the roads are bad now because of rain...i have a small language problem here and in person i do better than on the phone. 

i really do appreciate your help and i have to be wasting your time only to find out i have a bad iso image, a bad cd, and have to start all over again and then may find out i have a bad cd drive or a bad pc as well...

additionally i have this overclocking problem, i thought for sure i killed this creature this morning but it ressurrected itself once more. 

i have so many things going wrong i dont know which one to fix   first...

---

### Post by vivek40 on 2010-08-31
If your iso image file is in here as you said:-
[HTML]
/home/salima/Desktop/desktop folders/10.04 install disk
[/HTML]Do this:-
1.
[HTML]
salima@salima-desktop:cd Desktop/desktop\ folders/
[/HTML]just copy paste the above in your terminal.

2.then you will get this prompt in the terminal
[HTML]
salima@salima-desktop:~/Desktop/desktop folders$ 
[/HTML]3.At this prompt type 
[HTML]
salima@salima-desktop:~/Desktop/desktop folders$ md5sum ubuntu-10.04-desktop-i386.iso 
[/HTML]

It should give you the md5sum of the iso image on your file..

However I dont understand this

[HTML]
i burned it myself, took me four nights so it had to be paused and resumed,
[/HTML]
why should it take four nights to burn a cd.. anyways Brasero would definitely not have burnt it properly. I am very sure the iso image that you have downloaded will have the corect md5sum as mentioned on the site , but the cd should not have burnt properly.. try burning it again.It should not take you more than 5-10 minutes to burn an iso image
vivek!

---

### Post by varunendra on 2010-08-31
> **salima said:**
> ...i **can read** data disks, i **can play **commercial cd's,  i **can play **the copies someone made for me on cd-r disks. i dont have any other kind of disks to try...
-you mean you are able to read those discs successfully, right? Then you don't need anymore of them, this is more than sufficient to prove that the drive is okay.

> **salima said:**
> .... i have a bad iso image, a bad cd, and have to start all over again and then may find out i have a bad cd drive or a bad pc as well .....
i have so many things going wrong i dont know which one to fix   first...
:lolflag: ....too bad- feeling so much bad all at once.... :lolflag:

For the rest, if you suspect having a corrupt cd (which is my guess too) and want to download the iso again, **PLEASE use torrent this time** & download 32bit Desktop edition.
(Click [here]("http://releases.ubuntu.com/10.04.1/ubuntu-10.04.1-desktop-i386.iso.torrent") to download torrent, or,
Download from here: [http://www.ubuntu.com/desktop/get-ubuntu/alternative-download](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download), choose torrent please.)

And by the way, you may try one more time to search your original downloaded iso by searching all the **.iso** files on your drive (use **search** tool).

> **vivek40 said:**
> However I dont understand this
[HTML]
i burned it myself, took me four nights so it had to be paused and resumed,
[/HTML]........ downloading time?? maybe..?

---

### Post by salima on 2010-08-31
hi vivek-hi varun-

when i copy the command, here is what happens:
salima@salima-desktop:~$ salima@salima-desktop:cd Desktop/desktop\ folders/
bash: salima@salima-desktop:cd: command not found
salima@salima-desktop:~$ 

:lolflag:

sorry, i meant to say i t took me four nights to download the iso, not write/burn! i tried a bittorrent first, but it was  going horribly slow (even slower than my everything else) and one day i was trying to see how fast the alternate cd would go, since i thought it was a smaller file, but it appeared to be the same size and was also going slower. then i stumbled on  clicking on a link for a regular download, and it was going really good (a file that big for me should take about a week, not four days.) so i let i go through to the end and canceled the others.

i can try another download through bittorrent-

---

### Post by salima on 2010-08-31
oh, by the way...in the OP i mentioned the dbus error-doesnt that mean there is something wrong with the drive recognizing the cd? but i guess it could mean there is something wrong with the cd, not the drive...

anyway, i got the bittorrent download running so i at least i feel like i am doing something

---

### Post by varunendra on 2010-08-31
> **salima said:**
> oh, by the way...in the OP i mentioned the dbus  error-doesnt that mean there is something wrong with the drive  recognizing the cd? but i guess it could mean there is something wrong  with the cd, not the drive...

anyway, i got the bittorrent download running so i at least i feel like i am doing something
It means there's error in communication between drive & system, and either cd or the drive or both may be the cause. But since you said you are able to read all other discs, it becomes more likely that the ubuntu cd is defective.

A torrent download would make sure you get an 'intact' iso image, regardless of how slow your connection speed is or how many times it goes down.

Please confirm these:

[LIST=1]
[*]What is your conn. speed (based on this, you may have to manually set maximum no. of connections to accept, and upload speed limit).
[*]Are you downloading from the torrent I gave link of, or trying a different one? If it is a diff. one, please provide its link so that I could check it myself.
[*]What is the current download speed you are getting?
[/LIST]

> **salima said:**
> ....when i copy the command, here is what happens:
salima@salima-desktop:~$[COLOR=Red]** salima@salima-desktop:cd Desktop/desktop\ folders/**[/COLOR]
bash: salima@salima-desktop:cd: command not found
salima@salima-desktop:~$
....
:shock:....:roll:..........................=D>.. =D> ..=D>.............................](*,)](*,)

How about just copy-pasting the following command in the terminal:
```
cd ~/Desktop/"desktop folders"
```(assuming you have a folder on your desktop whose name is [COLOR=Red]**desktop folders**[/COLOR], and this is the folder that contains the iso image. If I'm wrong, please correct me.)

Again, assuming your terminal prompt (after entering above command) looks like [COLOR=Red]**salima@salima-desktop:~/Desktop/desktop folders$**[/COLOR] and you have md5sum installed, enter the next command as follows:
```
md5sum ubuntu-10.04-desktop-i386.iso
```The bottomline is, you have to be in the directory where the iso is, and since the folder name contains space, you have to use double quotes("") around its name while using the cd command.

---

### Post by vivek40 on 2010-08-31
Varun.. buddy.. you have real patience! :-)

---

### Post by varunendra on 2010-09-01
> **vivek40 said:**
> Varun.. buddy.. you have real patience! :-)

Click on "**-Varun**" in my sig to see why.. ;). Adding anything more could be dangerous here :lol:

---

### Post by salima on 2010-09-02
[FONT=monospace]hey varun-
i know i wrote a long answer to this, dont know where it went...i must have fell asleep.

[/FONT]   	 	 	 	 	 	  the file is in a folder called 10.04 install disk
 which is in a folder called desktop folders
 which is on my desktop
 

 are we getting anywhere yet?
 

 salima@salima-desktop:~$ cd ~/Desktop/"desktop folders" 
 salima@salima-desktop:~/Desktop/desktop folders$ md5sum ubuntu-10.04-desktop-i386.iso 
 md5sum: ubuntu-10.04-desktop-i386.iso: No such file or directory 
 

 do i not have md5sum installed? I will see what i can find out about that just in case
 

 Also, about the connection speed. I have BSNL Huwaei datacard EC325 and they say it is 230 mbps but i dont think so. When i watch the download windows the speed goes from 1-14 kbps. I tried to download the bittorrent again but after about 5 oor 6 hours all i had was 1.2 MB. I was using the link you gave me. There were times the speed went up to 21 kbps for the torrent load, but it was so erratic it would shoot back down to under a kb...is there a way to find out through my OS what is the true connection speed? I dont even have network manager as far as i can tell...

---

### Post by salima on 2010-09-02
update-
  	 	 	 	 	 	  i used brasero to check the md5sum and it gave me this error:
 the file integrity check cannot be performed
 no md5 file was given




i think i dont have that utility but i havent been able to find out how to get it...

---

### Post by varunendra on 2010-09-02
> **salima said:**
> salima@salima-desktop:~$ cd ~/Desktop/"desktop folders" 
 salima@salima-desktop:~/Desktop/desktop folders$ md5sum ubuntu-10.04-desktop-i386.iso 
 md5sum: ubuntu-10.04-desktop-i386.iso: No such file or directory
Hi Salima, nice to see you haven't given up.

The final output in your commands: **[COLOR=Red]md5sum:[/COLOR] ubuntu-10.04-desktop-i386.iso: No such file or directory **- is returned by md5sum itself (it is md5sum that is telling you the result) so _it is obviously there_. No problem with that!

However, as I said earlier, "You need to be in the directory where your iso file is.."
To make it happen, just enter the following command in the terminal:
```
cd ~/Desktop/"desktop folders"/"10.04 install disk"
```This should let you into the final folder where the iso is sitting. Afterwards, enter this command:
```
md5sum ubuntu-10.04-desktop-i386.iso
```To  avoid making any further mistakes, I think you should understand how it  works.

[COLOR=Red]**(WARNING: read it only if you are interested, otherwise it is perfectly safe to skip this section):**[/COLOR]
========================================================
First, always keep in mind that commandline in linux takes capital &  small letters of english differently. Now onto the cd command:

The cd command means "Change Driectory". There MUST be a space after a  command (which I think you already know). After cd, you have to tell the  terminal which directory you want to switch to. So you tell it in a  language it can understand. Note that terminal usually **doesn't accept space** in-between the address of a location. While your folder-names **do** contain spaces. So you need to **wrap each & every such name in double-quotes ("") that contains spaces**.  This makes terminal understand that it has to take that name as a  continuous string without needing to care about the spaces that lie  in-between those quotes. Now / sign in a path denotes a sub-level (which  you may read as- "in" if you are reading the path right-to-left).  Again, ~ denotes user's directory (user's home).
Now combining all of these we get : **cd ~/Desktop/"desktop folders"/"10.04 install disk"** which tells the terminal that: "Change to the directory **10.04 install disk** in **desktop folders** in **Desktop** in the user's** home**.

-so simple & easy! Isn't it ?? :twisted:
========================================================
Having (tried to) explain the command, I've to say that please don't  hesitate asking again if you still get errors (after all, it may save  you a lot of downloading time!).


 Now onto your download issue:
> **salima said:**
> .... they say it is 230 [COLOR=Red]**mbps**[/COLOR] but i dont think so.  When i watch the download windows the speed goes from 1-14 kbps. I tried  to download the bittorrent again but after about 5 oor 6 hours all i  had was 1.2 MB. I was using the link you gave me. There were times the  speed went up to 21 kbps for the torrent load, but it was so erratic it  would shoot back down to under a kb...is there a way to find out through  my OS what is the true connection speed? I dont even have network  manager as far as i can tell...
Whatever speed you are told by the ISP (BSNL in your case), just divide  it with 8 and you'll get the actual download speed that you **should **get  (however, it's not promised in most cases). Practically, on a 230 Kbps  (you'll be heavily taxed if you dared to even dream about 230Mbps i-net  conn. ;)) connection, the typical download speed on BSNL is 24-32 KBps.  So 21 KBps is just fine. If it goes below 18-20 KBps, then there are  certain things that may be going wrong- ranging from config. issues in  bit-torrent application to connection faults.

Nevertheless, I'd still suggest you to stick with torrent as it'll  guarantee an "intact" iso image that should easily pass the md5sum test.  And by the way, which bit-torrent application are you using? Is it  Transmission or something else?

I'd also suggest you to have a look at this (I've tried them once & found satisfactory):
([http://www.zyxware.com/requestcd?title=ubuntu](http://www.zyxware.com/requestcd?title=ubuntu) , Phone: +91-471-2449495 (O), +91-9446-06-9446 (M))

**PS:**
I think brasero can only check integrity of a physical disc, not an  image (I may be wrong though). So just go with the command line. If you  entered the command correctly, it'll return a code (detected md5value of  the iso image) which should be exactly same to that you got from the  download site.

---

### Post by vivek40 on 2010-09-02
No.... it does not work like this.... ok...I guess you should have md5 installed..see all the time you are doing the tests in the wrong folder..if your file is in here  as you say now:-


/home/salima/Desktop/desktop folders/10.04 install disk

then you have to cd to that folder for doing anything. What you are doing right now is that you are in the folder /home/salima/Desktop/desktop folders.
and that definitely does not have the file , so you get the result

"md5sum: ubuntu-10.04-desktop-i386.iso: No such file or directory"<-- is that not natural.. the file is not there so the computer says no such file .

. basically you have to go one more folder deep into "10.04 install disk".. so cd into that folder. 
ok so first open a fresh terminal:-
and type 
cd Desktop/"desktop folders"/"10.04 install disk" 
after that type this:-
md5sum ubuntu-10.04-desktop-i386.iso 

wait for a few minutes you will get your md5 sum.

(In the case of brasero, you should have clicked the option use md5 file check .. something like that.. what it requires is a file to check the md5 against.. so just do what is said above.. you should be fine.. this job of moving into a folder and doing md5 check takes a minute and you have already spent 3 days on it.... anyways!there is nothing to feel bad about it)

---

### Post by vivek40 on 2010-09-02
Oh.. sorry Varun.. did not know you had already replied!

---

### Post by salima on 2010-09-02
hi vivek and varun!
i dont want to give up because i want to know if i can do this or not...asking someone else to make me a cd doesnt teach me anything. and i know i have spent days on this but next time it wont take so long! in the beginning i know nothing, so everything more i do has to get easier. i loved ubuntu the first time i saw it and i would never go back you-know-where!

so basically both of you gave me the same instructions and i did it and this time it worked!
 the original hash thing i posted was wrong, it was for the 10.04.1 version-mine was the 10.04 and it is a perfect match!

salima@salima-desktop:~$ cd Desktop/"desktop folders"/"10.04 install disk" 
salima@salima-desktop:~/Desktop/desktop folders/10.04 install disk$ md5sum ubuntu-10.04-desktop-i386.iso 
d044a2a0c8103fc3e5b7e18b0f7de1c8  ubuntu-10.04-desktop-i386.iso

and from the howto page:
d044a2a0c8103fc3e5b7e18b0f7de1c8 
    ubuntu-10.04-desktop-i386.iso




i also retried brasero and checked the integrity of the disk and it told me that there   didnt seem to be any corrupt files on it.



 i wonder now if the physical disk itself has some defect...the burning was right but the disk is crap. in the meantime i also put in the disk for 8.10 and i didnt get any dbus error...it said there was software on there and it was all ready to roll.


so in that case, i should burn a new disk from the file we just checked? should i use something other than brasero? or am i going off in the wrong direction?

   	 	 	 	 	 	  I only have one disk...one disk with no manufacturer name on it. The one i used was a sony. I do have a couple cd rw's but i thought they would probably not be good to use. 



and thanks for the explanation, varun...it does help me to understand what i am doing, it makes it easier to apply something to other situations....


a small triumph! 

now, back to work...

---

### Post by salima on 2010-09-02
varun-
forgot to mention, the torrent file gave me only 1.2 MB in about 5-6 hours. i have shut it down for now. something is certainly wrong. also remember that i had to configure this modem connection myself, and i may have done something wrong. after i get my upgrade i can look into why i am not having any luck with these other things. oh yes, and i was using the Transmission clicent that came with 8.10.

that one i burned was the fastest i ever saw going through...maybe it is just a case of i need to get a fast connection, and the one i have is not only just slow, it is extremely erratic and unstable.

they tell me tata photon is a wireless fast connection. i want to avoid wires if i can, but i am afraid this is probably not available in ratlam-most things arent yet available here. i do plan to look into that when i get out of the house again though...the streets are dry now.

---

### Post by vivek40 on 2010-09-02
Cool.. that is great.. now the good thing is that you dont need to download the iso file again as the image is fine.. you just have to burn it properly.
There is nothing wrong with the disc . Any blank cd should do.. The problem occurs when we write an iso image file. Well personally speaking, I normally waste 2-3 cds because in my case brasero never writes a perfect iso image on a cd correct the first time. (but then this could just be my problem). 
My suggestion is to pick any blank cd and try burning the iso image on it properly using brasero.
I hope you know how to burn an iso image. You just have to click on burn image, select the image from the folder, after you open brasero (dont forget to put the cd in the cd drive). 
After the cd is properly written, do an md5 check on it. It should match the 2 md5s you have.
(yeah no one here would want you to go back to 'you know-where', checking the file integrity from brasero would not help. You will have to do an md5 check on the cd too, which am sure is not right, however to do that, again open a fresh terminal and type 
md5sum /dev/cdrom

---

### Post by varunendra on 2010-09-02
Nice to see we finally made some progress.
> **salima said:**
> i also retried brasero and checked the integrity of the disk and it told me that there   didnt seem to be any corrupt files on it.
From your first post, I thought the disk is not mounting at all. Your thread title confirms the same. So how did you manage to check the **disc**? Do you mean the iso image?


> **salima said:**
> varun-
forgot to mention, the torrent file gave me only 1.2 MB in about 5-6 hours. i have shut it down for now.
Now that you have checked the iso you already have to be consistent, I think you don't need to download it again.

For a cd burner alternative, I've heard good things about k3b (it is in synaptic). Apparently, it is perhaps the best free cd-burner for ubuntu. But its download size is around 79MB. So bet is yours.

I'd like to know precisely what you want to do now, and what are things you are not sure of regarding what you want.

---

### Post by vivek40 on 2010-09-02
K3b is definitely the greatest out there.. but installing it on gnome.. well I would not recommend that, it goes about installing a lot of kde stuff too alongside ...but yeah as varun said it is your call... My suggestion is to buy 3-4 cds,lol.. keep trying .. one will definitely write properly.. try at slow speeds(well that is what I do with brasero)

---

### Post by salima on 2010-09-02
hi varun and vivek! Ok-what i want is a good cd to do a fresh install over the 8.10, just put in 10.04, which means i will be back to hving no internet until i can get it configured again. I have no way of knowing if what i did in 8.10 will work in 10.04 to attach the modem...i can only hope

-i am already downloading K3b-is there anything i need to go with it? These files load way faster than getting something from the internet, i had to get all the gstreamers for my youtubes etc...they loaded like lightning.  

So my plan is to try K3b on the cd's i have left, and if that doesnt work i can go to the market in the morning if the weather holds up and get some more to try. I hope it is easy to figure out...before linux, i had imgburn, dvdflick, nero, some other thing and ashampoo, and ashampoo was the only one i could actually use. 


by the way...i always get the dbus error that the cd doesnt mount, and i just click ok and after awhile it appears to have mounted itself, but there is no way i know to boot at that point. Also i cannot see the file folders in it...very annoying, really. If i turn off the machine with it in the drive, it must again become unmounted so that the bios message to boot from cd is bypassed and the hard drive boots before the cd has been able to make its presence known. I know something is going on because the boot takes a lot more time, but it just ignores the cd. Is there a way to do a sort of shock boot without restarting? I mean if i do a restart, it is again unmounted...i think.so that is how i got to check the disk-it took me two or three tries, but eventually it was doing all the stuff and gave me the news it had completed the verification and there were no corrupt files. But that doesnt happen if i put in the 8.10 disk which i used to install what is running for me now-it just starts spinning and is ready to go.

---

### Post by salima on 2010-09-03
it worked...i downloaded the K5b thing and burned a new cd and it loaded fine.

i was pretty euphoric until i found out there is no wvdialer in lucid...i have no internet now and am typing from a cybercafe. the way i connected the modem was using wvdial so i have to see what else i can do, search the forum, start a new thread if i have to.

but thanks very much vivek and varun for your patience, i learned a lot doing this and i am glad i didnt have to ask someone to burn the thing for me.

---

### Post by varunendra on 2010-09-03
> **salima said:**
> it worked...i downloaded the K5b thing and burned a new cd and it loaded fine.

For me, it's joy of the week!! :D

For, dialling issue, assuming it is broadband through adsl modem, you've to use DSL tab of Network Manager:

[IMG]http://i621.photobucket.com/albums/tt292/varunjnp/DSL-1.jpg[/IMG]

In case of problems, you're of-course better-off starting a new thread.

Goodluck!

---

### Post by vivek40 on 2010-09-03
congrats.. so have you installed lucid... by the way in a month MM is out !:-)

---

### Post by salima on 2010-09-04
yes i now have lucid lynx!
 
i am not updating for three years it hink...stupid of me i forgot i was supposed to try this out and hook up ther modem before installing, that is the point of the live cd...but i was so excited when i saw it was there and ready to install, i hit the button!
 
yes, i am going to start a new thread i think in beginners' world...unless i find a more appropriate subforum. i am using a resurrected laptop that i removed half the programs already thinking i was going to pitch it...hope it lasts long enough to get my new post out there. i think i am halfway there to solving that problem, just a little help.
 
thanks to both of you for this one, i had great fun!

---

### Post by vivek40 on 2010-09-04
why dont you just do what varun has said above for connecting the internet through dial up.And as far as using internet while installing is concerned it is ok, even if you dont have internet connected at that time... after installing the cd , just do a sudo apt-get update and sudo apt-get upgrade after connecting to the internet.. you should be fine!

---

### Post by salima on 2010-09-04
hi guys-
it isnt dsl...i put the connection in wireless broadband and nothing happens, i had to go through this for about a week with 8.10. the solution using wvdial was great...all i need is wvdial. i will look at doing it through dsl, but i dont think it will work.

i did post a new thread in beginners, but because of my laptop being half formatted i could only attach the pdf file to the message. i dont know how to contact the moderators, so i hope they can open the file and paste it into the message. it is such a beautiful post, too...

also, i may have started two threads...i think the laptop quit on me before the first one went, but i didnt subscribe to the thread...i havent slept much in the last two days. hope to go make sure i dont have two new posts, and they will have to merge them-that already happened to me once, it is embarrassing...

---

