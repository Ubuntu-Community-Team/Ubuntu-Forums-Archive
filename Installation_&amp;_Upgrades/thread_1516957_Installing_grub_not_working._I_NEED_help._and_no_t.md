---
title: "Installing grub not working. I NEED help. and no terminal garbage please :x"
date: 2010-06-24
forum: Installation &amp; Upgrades
---

### Post by princerameses on 2010-06-24
I am trying to install puppy 5. I have tried before on a different computer with a different version and the same thing basically happened.

It says mount error when I try to install grub to \dev\sda6 or whatever. 

It said to follow the deafults except to install to MBR. Is this where I do that? I typed MBR and it said partition MBR is not linux. 

Can someone please help me? every time I ask for help on linux forums, my issues are never resolved. I just want to install puppy linux. :x

---

### Post by kalistona on 2010-06-24
of course !
do you want install XXXXX but where (usb/disq/dual-boot ?)
do you want as virtual or not (a real puppy installed or only see working ON windows) ?

it is very easy and ask 15 minutes.

---

### Post by princerameses on 2010-06-24
I would like to use the whole (internal) hard drive.

---

### Post by kalistona on 2010-06-24
have two disk or an usb free ? 
how could you install the .iso PUPPY on only one machine if you do not have a place to download and to install ?
if you are on another computer or from a cd or if the iso is on a usb key ?
or your are on ubuntu and you want put puppy [COLOR=Blue]with [/COLOR]?
or you are on ubuntu and you want [COLOR=Blue]only puppy[/COLOR] on your internal disk ?

---

### Post by darkod on 2010-06-24
> **princerameses said:**
> I would like to use the whole (internal) hard drive.

If you are installing it to the whole disk, why are you trying to install grub to the /dev/sda6 partition? How do you plan to boot it?

---

### Post by darkod on 2010-06-24
For installing on a whole hdd you really don't need to do anything special. Just tell the installer to use the whole disk (there should be such option in Puppy, not sure), and let it install grub to the MBR.

You are creating the issues for yourself it seems.

---

### Post by princerameses on 2010-06-24
^ This is why I need help. I do not know what I am doing.

And I should calrify: I took the hard drive from another computer which had Mandriva on it. 
I am using a live CD of puppy right which I am tryingt o install from.

I am on another computer right now.

---

### Post by princerameses on 2010-06-24
> **darkod said:**
> For installing on a whole hdd you really don't need to do anything special. Just tell the installer to use the whole disk (there should be such option in Puppy, not sure), and let it install grub to the MBR.

You are creating the issues for yourself it seems.

No I am not. It DOES NOT ask me to install to MBR. 

I tried just going through the install and it's not working.

---

### Post by darkod on 2010-06-24
[http://www.mygnulinux.com/?p=385](http://www.mygnulinux.com/?p=385)

---

### Post by kalistona on 2010-06-24
please tell us if you are on windows or ubuntu and  dd = how many go ?
maybe have you followed confused advices and all is not perfect ?

---

### Post by princerameses on 2010-06-24
I am on windows right now because I'm on another computer.. But the one I'm trying to install puppy to has mandriva installed. But I'm not on it; I'm on Puppy (live CD).

And I want puppy to be the only operating system.

---

### Post by darkod on 2010-06-24
The link I posted has screenshots. When you get to the step preparing the disk with Gparted just delete all existing partition and create new ones like in the tutorial.

If you still can't install with those screenshots, ask someone with more experience to help you.

---

### Post by kalistona on 2010-06-24
1°your machine must start from CD/DVD (and not from usually internal disk)  
you must go if you are on a laptop, with F2 or F8 inside your computer and choose : 
start from CD/DVD (it is an option up and down).
if you are not on laptop, the same thing exist, you must begin first here.
save your change and escape.

you start your computer and put the CD/DVD.

ok : you shut down the computer where you want install puppy keeping the CD/LIVE inside.
all is going be erased.
another system will be : puppy.

now it is beginning and you choose step by step all you need (langage etc..)
(you have a link just from darko read it please)
choose on the disk entirely .

and all is done in 10 minuts,  that is automatic,
you restart your computer and choose from internal disk and do not forget to put out 
the CD/DVD live before because now it is your new O.S.

---

### Post by princerameses on 2010-06-24
When I go to Gparted, it says unallocated space and says there's no partition table. 

If I select create new table, I don't know which type to use: MSDOS, gprt, BSD, ect. there was a long list. 

There is no option to use entire disk. It gives me two options: 7 GB and 44 GB. It's a 60 GB hard drive. 

I'm really getting upset. Why do they make it so difficult? Ubuntu is easy to install. Why can't puppy be?

---

### Post by kalistona on 2010-06-24
gparted ?
if 'no allocated files' it means that it is free so you can choose this one for puppy.
i do not understand what do you want.
it is really very easy and all; even mandriva ubuntu and the others; are, the most often, in the same choices ...
whre is the problem ? in the choice of allocated file, in the choice 'entirely the disk '
well choose another option like this partition or 'the more space it can or side by side and you shoud come back in few days  and will do a better installation but for today try an option please.
you are not in OEM is n't it ?

---

### Post by princerameses on 2010-06-24
It won't let me do anything. 

It says there's no partition table.

I have installed ubuntu, mandriva, PClinux OS. All were very straight forward. Unlike puppy, damn small linux, Vector, and the other small ones I've tried.

I think I've had just about enough. I think I'll go put my windows hard drive back in.  It keeps freezing which is why I wanted linux.

And puppy is the only one that will work with my video card/ monitor. :(

---

### Post by darkod on 2010-06-24
It's MSDOS partition table you want. Puppy installer does require little more interaction from the user than ubuntu. But you also need to know some basics before trying to install an OS. They can't do everything for you. :)

---

### Post by kalistona on 2010-06-24
i see only one solution : contact [COLOR=Blue]puppy site help[/COLOR] they are kind and gentle, they can straightly install it or with [COLOR=Blue] angel[/COLOR] very easily. be confident and join them please.
thank you for your post it was nice to help you. so long.

---

### Post by princerameses on 2010-06-24
Well wait, I tried doing the table following the guide, and I got an error for the ext3 partition. #-o

I've tried the puppy linux forums; they are too slow.

---

### Post by princerameses on 2010-06-24
Is there a safe bootable program that I can use to erase the hard drive? 

Maybe if I do that things might work. Because it's talking about 30 gb in gparted, but it's a 60 gb hard drive..

---

### Post by kalistona on 2010-06-24
ok it is not an error it means that it is bad done.
ext 3 is created automatiquetely (excuse i am french) so you have done something that the machine have not understood the orders, maybe not the same; that you have given.
what do you want to do now ? here it is 19h20.
will you install it today or see in another place, why not at the puppy site ?, sure they are here for help and they are kind !

---

### Post by princerameses on 2010-06-24
I don't know.. I think I'll end up just getting a new monitor and install xUbuntu. Because this is crazy.

---

### Post by kalistona on 2010-06-24
you could go see to gull or parrain-linux or see an install party, all these persons will do it free for you in less 15 minuts in front of you. good journey princess.

---

### Post by princerameses on 2010-06-24
Where does the jumper need to be on the HD to make it slave? 


If I can have the windows HD as master and the other one as slave, I can format that disk using windows.

If I can do that I'll try once more to make puppy work.

---

### Post by kalistona on 2010-06-24
where is your first disk ? on windows ? click desktop and choose the disk that you want format (the disk that you are not in, free) click right format.

if you do not understand or you cannot, try proprieties (of the disk that you want format) and format in FAT32.
then install on this one the puppies (pupies will format for you in ext3 from fat or ntfs). 

slave and master does not really make a differene because anyway you will have the choices between two disk.

---

