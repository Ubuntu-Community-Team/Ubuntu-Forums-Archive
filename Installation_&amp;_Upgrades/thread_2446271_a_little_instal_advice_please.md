---
title: "a little instal advice please"
date: 2020-06-27
forum: Installation &amp; Upgrades
---

### Post by imsoslow on 2020-06-27
Hello everyone , im hoping to learn a little something today about instal.
First ....


_Equipment _
Dell desk top 
Win XP SP2


_C drive_ = 80 Gb running Win Xp ok


_E drive_ = partition 1 of 2 is 58 GB ,, free space 


_F drive _= partition 2 of 2 is 53 GB of files to keep 


OK .. I want too instal Lubuntu in the E drive, but keep windows XP as i need it from time to time. 
Im having a lot of problems with failed instals , i may need som advice .
I have Lubuntu on a 14Gb flash drive along with a program called UNETBOOTIN , which allows me to run from the flashdrive.
what would be my best options .
Please use small words as i dont understand Linux , and im fairly thick as a person anyway.
maybe i cant do this or im confused.
Thank you

---

### Post by oldfred on 2020-06-27
Windows confuses drives & partitions. You probably only have one physical hard drive and a flash drive.
But have multiple partitions on the hard drive.
With Windows a d: "drive" may be a second partition on first physical drive or first partition on second physical drive.
With Linux drives are clearly shown as sda, sdb, sdc etc and partitions are the numbers after the drive like sda1, sda2, sda3.

You do not mention a d: drive, so best to see exact partitioning from Ubuntu.
Open a terminal in the live installer and copy & paste this into terminal. Copy & paste output back to forum. If more than a very few lines use Forum's advanced editor (Go Advanced) and highlight the output and click on the # to add code tags to preserve formatting & make it easier to read.

sudo parted -l

copy & paste command as -l is an el, not I nor 1, many try to type and use wrong char. Depends on font used how much it looks like lower case L.

---

### Post by imsoslow on 2020-06-27
Dear Mr OldFred
Hi  ,, thanks for the reply ,
first thing is, the drive info I put up is correct . there are 2 drives, one with a partition , i know this because i put it in myself some years ago
However , thank for the linux drive labelling , I did see those type of names come up, but wasnt sure what they meant .
So i may have something like 
sda then sdb1 and sdb2 for example ?
Ah the D drive , i did not put that in as that is the DVD writer (DVD-RAM driveD)
there is another drive i missed out as i thought it was not important,, A (3 1/2 Floppy)


I did try to do an instal from the flash drive , and it seemed to go well , then i got an error and it could not continue, damn , after that andi had to abort , i went back to windows and found that I could no longer see that drive ,, so 58 GB of space are missing ! 
i was thinking of taking the info out of the F; part onto a portable drive and then just reformatting or putting the whole drive back into one .
so E; and F: would just be one big drive of NTFS and maybe putting Lubuntu into that, in that way if anything went wrong I would not loose any of the files in F: 
they could be reuploaded later on .


The idea is to make a dual boot computer, still running good ole , WIN XP ..
but I can boot into Lubuntu if I want ,, maybe in a year or so , just loose the windows part  but for the moment ..DUAL 
im back on the WIN XP now to write this 


what would be my next move? it seems every time i do something i make it worse for myself.


PS .. after the instal atempt i notice now using a partition tool in windows , that i may not see part of the drive as it has became ExFAt .. the instal reformatted that !!damn .. i havnt re booted to see if Lubuntu can see it yet . 
also each drive has a small 10 Mb unallocated bit , that windows must use for something ...
What a mess ive made

---

### Post by oldfred on 2020-06-27
Need to see partitions.Then may be able to make specific suggestions, not generalized ones that you may not understand.

I would not expect Lubuntu to change anything to exFAT. The exFAT driver has to be added for it to even know about that. Your third party Windows tools may have done that?
XP needs to be NTFS as I remember, but have not used XP for 10 years. 

I dual booted from 2006 to 2010 with XP & Ubuntu on my Dual Core Intel based system.
The one XP app that I kept after install of Ubuntu I really liked. But the Linux app was functional, just not quite as good. But not worth all the hassle of weekly booting into XP to run app and needing hours of updates.

But you really should not run XP unless not even connected to Internet. You will get hacked.

---

### Post by imsoslow on 2020-06-27
oops

OK , I also do not know why the exFAt came about but win does not see it , however a tol called ... mini tool partition wizards finds it ok and tells me theres 145 Gb of exFAt now ... i dunno why but thats annoying the lubuntu instal was from the lubuntu program itself , i can click on ,,instal lubuntu from the (lubuntu ) desktop 


as to not running XP , i do need it for now and my wife is used to some things on here , so for the moment i can use it . 
dont worry about me getting  hacked 
i still need to get lubuntu installed , but now i need to fromat the whole spare drive back into one , make it all NTFS.
I suppose that is first ...
when thats done try again to instal without it turning to exFAt

---

### Post by imsoslow on 2020-06-27
well ok,, i got my partition back 
i now have ,,, all on the same spare drive 
E; NTFS 58 Gb empty
F; NTFS 53 GB 18% used 
K : 8 MB NTFS ,, a small partition left over  from a previous installation of windows 




So now, I would like to get Lubuntu installed from the flashdrive into  drive E; NTFS 58 Gb empty


is this possible? and on computer boot up i will then have a choice ( as i do when i put the flash drive in.. Lubuntu or Windows..
next move?

---

### Post by oldfred on 2020-06-27
E: is Windows, it will not show as E:, so you have to know what it will look like in the installer.

Post the parted output to see partitions.

---

### Post by Impavidus on 2020-06-28
> **imsoslow said:**
> 
i was thinking of taking the info out of the F; part onto a portable drive and then just reformatting or putting the whole drive back into one .
so E; and F: would just be one big drive of NTFS and maybe putting Lubuntu into that, in that way if anything went wrong I would not loose any of the files in F: 
they could be reuploaded later on .
Copying everything to a portable drive would be a very good idea. Although it's possible to install Lubuntu on that harddrive without loosing the files on the F partition, it's not unlikely you'll make a mistake and loose the entire F partition instead. And even if you don't make a mistake, you could loose the files if the harddrive breaks. So, yes, make sure you've got those backups.

---

### Post by imsoslow on 2020-06-28
[ATTACH=CONFIG]286333[/ATTACH]old fred

errm , no 
C is windows , as in my first post thus 
_C drive_[COLOR=#000000] = 80 Gb running Win Xp ok[/COLOR]


_E drive_[COLOR=#000000] = partition 1 of 2 is 58 GB ,, free space [/COLOR]


_F drive _[COLOR=#000000]= partition 2 of 2 is 53 GB of files to keep 

so E is free space and shows as E 
so what im trying to do is instal Lubutu on E , and leave everything else as is .
then i get to choose on bootup , Win or Lubutu


[/COLOR]

---

### Post by imsoslow on 2020-06-28
Lmpavidus.........

yes , that is done . all saved and copied 

so im just having a problem with the instal of Lubutu on E drive 
I cant seem to intal it either from the flash drive or.. from the program itself , when its running , even though i have that option it failed, and everything went south then , so im trying to work out why , before i try again ,
hence the instal advice post ..
thats it

Sorry forgot to mention its Lubuntu 18.04 that i have , in case that is important info as well

---

### Post by oldfred on 2020-06-28
As I said you do not have an E: drive in Linux.

Post this from live installer:
sudo parted -l
lsblk -f

---

### Post by Impavidus on 2020-06-28
That "E: drive" is only known as "E: drive" by Windows and as long as Windows knows what it is. After you installed Lubuntu there, Windows will call it an "Unknown partition" and Lubuntu will call it /dev/sda1 or /dev/sdb2 or something like that.

Maybe it's best to simply delete that E partition using Windows tools. The installer will offer to "Install Lubuntu alongside Windows", which will probably do what you want (i.e., install Lubuntu in the unallocated space that used to be the E partition), but as you have multiple hard drives, that option is a bit unpredictable and may the the cause for your original failure. It may be better to choose "Something else", which allows for manual partitioning. Then you can create a new partition for Lubuntu and select the device for the bootloader. If oldfred agrees with me.

Lubuntu 18.04 is fine, although I would use Lubuntu 20.04. 18.04 has less than 10 months of support left, but you can choose to deal with that later. Once you managed to install one release, you can repeat the trick with the next.

---

### Post by ajgreeny on 2020-06-28
You have shown us an image of the partitions from your Windows system.
Now boot to the live Lubuntu flash drive, open gparted from the menu of that and again show us an image of the gparted window.

We really do need to see what Lubuntu sees, not what Windows sees in order to help you more so please try to do what is suggested and do not keep on talking in Windows terms as that is not very much help, as several others have already said.

---

### Post by imsoslow on 2020-06-30
Well I do have the E drive in linux ... meaning, the drive is there , its just not called E .. its ../dev/sda1 or something, and that the space that I wanted to instal Lubuntu but couldnt. ...


If i could put Lubuntu in it , i dont mind what windows calls it , i think it will still call it E as that was the letter I gave it , but never mind , what windows calss it is not really important.


Impavidus
I thnk i get what you mean, but i made the E partition to put Lubuntu in , specifically .. the other half of that drive (F) has stuff in id like to keep .. however i have a portable hard drive copy of it .. so no biggy if it ghot deleted in the instal.


unpedictable is a word i dont like in computing .. I did try the instal using " something else" .. so then you suggest i make a  new partition inside the partition that was made for lubuntu..? !
I suppose i could .. why not ..
now ,,,could you clarify the bit about ..." select the device for the bootloader" that bit confuses me . try to use small words :)


I chose 18.04 as someone (online) said it was better for the old system i have ,,, but if I can stick on 20.04 .. ill download it and just go straight for that maybe..

---

### Post by imsoslow on 2020-06-30
ajgreeny  
Ok .. sorry about the windows stuff .. thats just me trying to relete something i dont know , yet , to another thing .. i shall neveer mention it again ... 


Ill re boot into Lubuntu and get right on it the best i can

---

### Post by imsoslow on 2020-06-30
[ATTACH=CONFIG]286377[/ATTACH]I find it hard to do screen shot , sorry 
also , i think the reason for Lubunu 18.04 instead of 20.o4 was because its 20 is 64 bit

---

### Post by oldfred on 2020-06-30
Is you system not 64Bit?
And 555 bad sectors is not a good sign.

May be time for a new system, or at least a newer used system?

---

### Post by Impavidus on 2020-07-01
Using the option "something else", you can select /dev/sda1, give it mountpoint / (root), filesystem type ext4 and mark it for formatting. Make sure the other partitions are not marked for formatting. Install the bootloader on /dev/sda. Windows appears to be installed on the other harddrive, so that would put the Windows bootloader on one harddrive and the Lubuntu bootloader on the other. Set your bios to boot from the Lubuntu drive and you should get a menu offering a choice between both systems.

But this is only a short-term solution. A few things are worrying:
- Your hard drive appears to be near the end of its life.
- Lubuntu 18.04 only has about 9 months of support left. Are you sure your computer doesn't support 64 bit? Many computers from the WinXP era support 64 bit, although they had a 32 bit Windows system. I think I mentioned that in your previous thread.

---

### Post by ActionParsnip on 2020-07-01
If you delete the partition that is occupying the space you want to use for Ubuntu (This will destroy the data on it so be sure to backup whatever you need from it). You can then tell the installer to use the unpartitioned space. As Windows XP doesn't have the UEFI/Secureboot rubbish to worry about this will be managed and GRUB will handle the boot for you

---

### Post by imsoslow on 2020-07-01
oldfred
Nope this is X86 , which is 32 bit , but that is the whole point , i'm making a dual boot, and my first Linux system to learn on from this computer .. 
well hopefully , if i can 
as to the bad sectors , i can sort them out, the disc has been chopped and changed and reformatted and the recent jaunt into Lubunu that failed caused a exFAT config , i don't yet know why , but i may straighten it all out and remove some of those old partitions , this was originally the old hard drive from and earlier computer running another system that cannot be named.
I'll get around to it , 


Impavidus
Ok ,, thank you for writing back .. this is it .. i think i understand 
use "something else" option
root is ../dev/sda1
bootloader is ... /dev/sda. 
..and yes , i wanted Win left on that hard drive .. (for the moment ) and Lubuntu on the other , then I can learn about it a bit more.


Ok , so the 32 / 64 bit thing .. I'm fairly sure mine is 32 bit only as the system info gives ::x86 Family 15 model stepping 1 intel 2992 Mhz
so based on that ... it wont be worth changing ,,, a new 64 bit processor means a new mother board and everything ,,,extensive surgery ,,,,
so ,, bin ,,, and get a new computer, I have to admit though, for its age its actually doing pretty well.. anyway
due to this, it gave me the idea of running Lubuntu along side it and about 10 months to get used to it ..  eventually , I suppose I will have to admit defeat on it , but when that day comes ...i will be able to hold my head up high and say ...I tried .. and i never gave up... i upgraded ..i changed and swapped .. i learned ,, and i even went into the world of Linux , and came out a stronger man ....
Legends are made of this stuff ....


 sorry .. got a bit distracted there ... back to the instal .... 
Ill try again soon .....




ActionParsnip
Yes already did that ,,,, in fact all the partitions on that drive ,, of which i see there are now 5 , for some reason ,,, could all become one ... one with each other , and the universe .. 
but i would like to keep partition 2, if possible ,, but if it has to be sacrificed for the greater good ,,, then so be it .. 
I have a copy .. but this is still a learning thing as well ....


I shall follow the advice of Impavidus soon ,,, wish me luck ,,, this could all go very wrong ,,,
thank you all for your advice ...

---

### Post by ActionParsnip on 2020-07-01
Be sure to run a full backup before you do most things (if your data is important)

---

### Post by imsoslow on 2020-07-01
i made a copy of most stuff i need onto a portable hard drive, after that im good to go , , if it works out well i'll delete the windows drive and just leave lubuntu ... but small steps first i think ............. is my first post using lubuntu where i managed to connect to internet and find this site ... although its still on USB drive at the moment .... but im sure you can tell .....:)

---

