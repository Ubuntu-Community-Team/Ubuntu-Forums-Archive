---
title: "Problem installing vista"
date: 2008-01-07
forum: Installation &amp; Upgrades
---

### Post by tylerdurden15 on 2008-01-07
I am running linux right now and love it but want to have vista or at least xp for a back up.  I tried installing vista and got this error code when coming to choose what partition i wanted to install it on.  

Windows could not assign a drive letter to a partition on disk 0. The error occured while preparing the computers system volume. Error code 0x80004005.

I know this is kinda a vista problem but any help i would appreciate, im guessing it has something to do with linux.

THANKS

---

### Post by snakeeyes on 2008-01-07
Hi, if u want to install Vista over Linux then u will need to remove Linux first or repartition ur disk to create free space and then format that with the NTFS file system and install Vista. After that u will need to reconfigure GRUB as well. Its difficult. The easy way is delete all partitions and then install Vista and then reinstall Linux.

---

### Post by tylerdurden15 on 2008-01-07
How can i totally format my hard drive deleting linux and starting fresh?

---

### Post by snakeeyes on 2008-01-07
Boot up using Vista setup disc and delete all partitions, create new ones and continue installing Vista.

---

### Post by tylerdurden15 on 2008-01-07
I can't thats the thing, its just asking me what partition i want to install it in.  It gives no option to format and make new partitions

---

### Post by Balazs_noob on 2008-01-07
you could download and use a Gparted-livecd for formating
i love it ;)
it boots up like ubuntu live mood but the only app you will have
is gparted...


here is hte link
[http://gparted-livecd.tuxfamily.org/index.php](http://gparted-livecd.tuxfamily.org/index.php)

---

### Post by snakeeyes on 2008-01-07
Yeah download gparted and use that, but just to make sure u do have a new install version of Vista right, not the upgrade on?

---

### Post by tylerdurden15 on 2008-01-07
Yeah i have both, i have using the vista install but i also have the ugrade.  I decided to try to install xp then upgrade to vista but now the xp disk freezes right when the prompt to install comes up.

---

### Post by tylerdurden15 on 2008-01-07
all i wanna do is delet linux install windows the re install linux  how can i do that in that order?

---

### Post by snakeeyes on 2008-01-07
Ok, if u know ur hard disk manufacturer's website then download the diagnostic tools and completely erase ur hard disk from those, or try kill disk. Then install Windows Xp. Upgrade to Windows Vista. Now continue installing Linux. If u use ur hard disk diagnostic tools except of kill disk then also run a scan on ur hard disk for errors.

---

### Post by tylerdurden15 on 2008-01-07
my hard drive diagnostic dont work on linux of course. im going insane

---

### Post by snakeeyes on 2008-01-07
Cant u like boot up with the diagnostic tools or something? Ok try this boot up with the LInux live cd and delete ur partitions through there.

---

### Post by tylerdurden15 on 2008-01-07
I'm going crazy trying to figure this out.  I wanna use the kill disk after all else fails, but thanks

---

### Post by tylerdurden15 on 2008-01-07
Alright i will try that when i get back from the gym.  I finally got the xp cd to work and it says it cant find ANY hard drives which seems really strange.  What would make it sya that when i obviously have a HDD in there.  I think fixing this would fix all my problems.  

If i repartion the HDD from the linux live what exactly should  i do? Like how do i make a seperate partion that will work with windows, is there any extra button i have to click or something i can type?

THANKS!

---

### Post by snakeeyes on 2008-01-07
Make them fat32 partitions.

---

### Post by tylerdurden15 on 2008-01-07
Alright im at the point on the live cd where i can manually partition the drive. should i move linux? and whats mounted?  Should all the drives be mounted? And whats with the root partition "/"?? I am so confused i just want this to work, with linux installed first apparently your screwed for a dual boot.

---

### Post by tylerdurden15 on 2008-01-07
Also i am seeing alot of /dev/**hda5**, my hard drive says sda.  Is there a differnce? and is the reason none of this is working because of that?

---

### Post by snakeeyes on 2008-01-08
> **tylerdurden15 said:**
> Also i am seeing alot of /dev/**hda5**, my hard drive says sda.  Is there a differnce? and is the reason none of this is working because of that?
no that shouldn't have any effect, sorry for the late reply.

---

### Post by zetetic on 2008-01-08
> **tylerdurden15 said:**
> I can't thats the thing, its just asking me what partition i want to install it in.  It gives no option to format and make new partitions

Well, it seems Windows Vista is not ready for the Desktop. Ask Microsoft for a refund.

Vista install CD should have a partition editor and should be able to format any partitions, just like Ubuntu Live CD or Debian Live CD.

Vista should also allow you to install it to any partition, and not only to the first partition on the hard drive.

So, I repeat what seems evident: Windows Vista is not ready for the Desktop. Ask Microsoft for a refund.

cheers,

zetetic

---

