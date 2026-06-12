---
title: "Home folder from old install on a different partition"
date: 2017-05-28
forum: Installation &amp; Upgrades
---

### Post by joseph123321123 on 2017-05-28
I hope I am posting in the right place.

I recently Installed Ubuntu 17.04 64 bit on a partition of my hard drive. It's about 30GB. I have 16.10 32 bit installed on a partition that is 441GB. My 16.10 has been upgraded a few times since the version that I originally installed, I think it was 12.04. It isn't *clean, *some things are buggy. I have started using the 17.04 installed on the 30GB partition and it is running smoothly. The main difference is that Unity is running way faster than on my 16.10 install. I think that is most likely as it is a clean install not an upgrade. 

Anyway, what I am trying to do is to have the 16.10 441GB sda6 partition as my home folder in the 17.04 30GB sda7 , so that when I click on nautilus the panel has documents, downloads, music, etc from the 441GB volume.

I have an external HDD, however it's ancient, it copies at really slow speed. If I had a good external HDD I would just copy all the important stuff to it and the transfer it. However with the HDD I have that might take days.

I have found a few things after searching google for an hour or two, however much of it seems to be about having a separate home folder partition, which in retrospect seems a great idea, however isn't really possible now.

Essentially what I'm trying to do is simply to get my home folder on the 17.04 30GB sda7 to have the contents of the 16.10 441GB sda6. Is it possible? 

Help would be much appreciated with this.

Thanks

---

### Post by yancek on 2017-05-28
There are multiple ways to do that, depends on what you want.  If you want the 440GB partition you can put an entry in the /etc/fstab file for it.  You can find numerous sites with examples and I'm sure numerous posts here on these forums.  Doing this would have the entire install of 16.10 available.  If you only want the /home directory for the partition, you can shrink that partition for 17.04 if it is not mounted and move the /home data to the new partition.  You will need an fstab entry for it also.  If 17.04 is working fine and you don't want 16.10, you can simply delete everything on that partition except the /home directory.  Probably other ways to do it, depending upon your end goal.

---

### Post by joseph123321123 on 2017-05-28
[SIZE=2]Hi Yancek, thanks very much for your reply.

I tried installing 17.04 again and setting 'home' directory as the old partition. 
The instructions on this post [https://ubuntuforums.org/showthread.php?t=1492938](https://ubuntuforums.org/showthread.php?t=1492938)

When it installed though the home folder wasn't the old folder and also I couldn't actually find the volume. I don't think it was mounted.

I have installed again and now the partition is in the launcher.

I think this link is probably similar to what I should be doing, however  there are a few things that I don't really understand.

[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

> # (identifier)  (location, eg sda5)   (format, eg ext3 or ext4)      (some settings) 
UUID=????????   /media/home    ext3          defaults       0       2 
The second line make sense, I don't know what to I should put in the some settings or identifier though



*Also*

> **Copy /home to the New Partition**

[COLOR=#333333][FONT=Ubuntu]Next we will copy all files, directories and sub-directories from your current /home directory into the new partition. If you do not have an encrypted home file system, just do the following:[/FONT][/COLOR]

sudo rsync -aXS --exclude='/*/.gvfs' /home/. /media/home/.


I don't really understand that. I wouldn't be able to copy from the sda6 to the sda7. When it says 'current home directory' would that be the directory of 16.10 or 17.04??

Having the partitions the size that they are now would be ok, the end goal is to be able open nautilus and open the files in 16.10 from there.

Is this the sort of thing I should be doing?
[/SIZE]

---

### Post by Bucky Ball on 2017-05-29
I'd suggest you create symlinks in the /home folder of 17.04 to the folders in 16.10. This is VERY easy and will save you much time. The caveat is that you will need the 16.10 partition mounting at boot and for this you will need to edit the fstab.

So, symlink syntax. This is ALL done booted into the 17.04 install. You will not need to boot to the 16.10 install, just have that partition mounted.

Lets say your 17.04 /home folder is at /home/username, where 'username' is your username, and you have a documents folder at /media/17.04/home/username/Documents. The syntax for a symlink goes like this:

```
ln -s 'location to link to' 'name of symlink'
```

Consequently, you'll want:

```
ln -s /media/17.04/home/username/Documents /home/username/Documents 
```

[See this page]("http://www.herikstad.net/2009/07/creating-symlink-in-ubuntu.html") for further detail. Hope that helps. As yancek mentions, there is more than one way to achieve what you're after, but symlinks are one method that is commonly used.

When you have created the symlink, your will be left with /Documents and a shortcut to the Documents folder in 16.10, also called 'Documents'. Delete the /Documents FOLDER, NOT the /Documents symlink in the 17.04 /home/username folder.

Hope that helps. :)

PS: What you should be doing to mount the 16.10 partition at boot it this. Open a terminal, run this.

```
sudo blkid
```

Take note of the UUID number for the /dev/sd** of the 16.10 partition you are wanting to add to fstab. Then open this file:

```
sudo nano /etc/fstab
```

At the bottom of that file, add something like this:

```
# Entry for my 16.10 partition
UUID=<add UUID number here> <mount point here>   ext4    errors=remount-ro       0       1
```

As an example, here's one of mine.

```
# /dev/sdb10 Data
UUID=0cdd1989-6b0d-48fe-a5a8-2b8ae640dcc1 /mnt/storage    ext4    errors=remount-ro       0       1
```

So, as an example, just say you have the same UUID number for your 16.10 as I have in the above example, you would use something like this if your mountpoint for the partition in 17.04 was, say, /media/16.10:
```

# Entry for my 16.10 partition
UUID=0cdd1989-6b0d-48fe-a5a8-2b8ae640dcc1 /media/16.10    ext4    errors=remount-ro       0       1
```

Hope that makes sense. Feel free to ask questions. ;)

PS: Anything after a # in the fstab, or any file, will not be read by the system. It is for comments only (which some of us humans require!) so write there whatever is best for you.

---

### Post by joseph123321123 on 2017-05-29
Hi Bucky Ball,

Thank you very much!

I've made all the symlinks. It was actually really easy to do.

I think this is probably obvious but how do I now delete the Documents folder? Can I do it from the terminal? If I go to home and right click on it I can send it to the rubbish bin, I'm guessing that would also delete the symlinks though?

EDIT: Also I think that the 16.10 partition might be mounting at boot automatically, it is always there in the launcher. I don't know if that might make things any easier?

---

### Post by Bucky Ball on 2017-05-29
> **joseph123321123 said:**
> I've made all the symlinks. It was actually really easy to do.

Excellent. Well done. ;)

> **joseph123321123 said:**
> I think this is probably obvious but how do I now delete the Documents folder? Can I do it from the terminal? If I go to home and right click on it I can send it to the rubbish bin, I'm guessing that would also delete the symlinks though?

Firstly, if the symlink has the same name as the original 'Documents' you should now have two folders called 'Documents' in the /home/username folder, but one is not a folder, it is a symlink. A shortcut. 

As such, if you look closely you will see a little arrow or something on it to indicate it is a symlink. Failing that, right click and it will show it is going to the target directory on the 16.10 drive. If not, then it is the original Documents folder.

Secondly, to delete the Documents folder (the original 17.04 Documents folder that should be), simply right click and delete. 

Before doing so, you should copy what you have in the original Documents folder, if anything, into the symlink (which in reality puts it in the Documents folder on 16.10 partition) then delete the original Documents folder. No, that will not delete the shortcut/symlink as they are not connected in any way, or at least shouldn't be if you have done this correctly. 

You should be left with a Documents folder on the 16.10 partition and a symlink to it in the 17.04 /home folder. The original 17.04 Documents folder should be gone.

> **joseph123321123 said:**
> EDIT: Also I think that the 16.10 partition might be mounting at boot automatically, it is always there in the launcher. I don't know if that might make things any easier?

Ah ha. That would depend on which you've made the symlink to. ;) You're going to need to check on that. I usually manually create a mountpoint in /mnt folder and mount things in fstab to that, as per my example earlier:

```
# /dev/sdb10 Data
UUID=0cdd1989-6b0d-48fe-a5a8-2b8ae640dcc1 **/mnt/storage**    ext4    errors=remount-ro       0       1
```

The system generally automounts external devices to /media and that will NOT show up in fstab 'automagically'. It just mounts it.

Have you created your symlinks to a folder in the automounted partition in /media? If so, make sure you make the fstab entry for the correct one. It will probably be /media and if the system has the partition automounting it may work without the fstab entry. 

Experiment and improvise. If you can boot your machine and the symlinks are working without you needing to manually mount anything, then yes, that's going to make things easier. If not, edit /etc/fstab. If you give the output of 'sudo blkid' and let us know the partition you are going to mount we can help with that if you need it. ;)

---

### Post by joseph123321123 on 2017-05-29
Thanks again Bucky Ball.

To make the symlinks I found the file paths in the 16.10 partition, so documents was '/media/joe/e6a6e484-e99c-4f85-a370-0c640b5b1e76/home/joe/Documents' and then in terminal I did 

'ln -s /media/joe/e6a6e484-e99c-4f85-a370-0c640b5b1e76/home/joe/Documents /home/joe/Documents'

I thought it was odd that the UUID was in the file path but the symlinks are there now. The file path for the 16.10 documents is '/home/joe/Documents/Documents'

> [COLOR=#000000]Secondly, if the symlink has the same name as the original 'Documents' you should now have two folders called 'Documents' in the /home/username folder, but one is not a folder, it is a symlink. A shortcut. [/COLOR]

The thing is the symlinks aren't in the home folder.The home folder has the 17.10 desktop, documents, downloads etc, however no symlinks. Damn! 

Could I move the symlinks to the home folder and then delete the originals?

I've made two screenshots also

[https://ibb.co/mvYnca](https://ibb.co/mvYnca)
[https://ibb.co/eU2Vxa](https://ibb.co/eU2Vxa)

The 'sudo blkid' output is 

/dev/loop1: TYPE="squashfs"
/dev/sda1: LABEL="System Reserved" UUID="8686FD1C86FD0D85" TYPE="ntfs" PARTUUID="0006e838-01"
/dev/sda2: LABEL="Windows 10" UUID="59E47082058140E2" TYPE="ntfs" PARTUUID="0006e838-02"
/dev/sda5: UUID="8ae77fdd-15a3-43e7-8508-8c7aa0acefc4" TYPE="swap" PARTUUID="0006e838-05"
/dev/sda6: UUID="e6a6e484-e99c-4f85-a370-0c640b5b1e76" TYPE="ext4" PARTUUID="0006e838-06"
/dev/sda7: UUID="13cf7101-a1b7-40c3-ae3f-01db6bb5fca1" TYPE="ext4" PARTUUID="0006e838-07

---

### Post by Bucky Ball on 2017-05-29
Ok, I have no idea here as i don't see either install labelled, but I'll guess that 16.10 is /dev/sda6. You can check this with Gparted if you have it installed or Disks I think. 

Yea, your symlinks should probably be working, but bit long-winded. You're linking to the automounting /media directory path and if you're happy with that and it's working for you, all good. Easier would be at the bottom of the fstab file, something like:

```
# /dev/sda6 16.10
UUID=e6a6e484-e99c-4f85-a370-0c640b5b1e76   /mnt/storage    ext4    errors=remount-ro       0       1
```

You could call mountpoint for the 16.10 partition /mnt/storage or whatever you like, but whatever you call it, you'll need to create that mountpoint manually where you want it in the 17.04 install pre creating the fstab entry. * Edit Use /mnt.*

Then, your symlink would look something like:

```
ln -s /mnt/storage/Documents /home/joseph/Documents
```

I'm going for a lot of guesswork there and only you know the correct paths so will need a bit of nutting out if you go that way. If you're happy, stick with what you've got. I don't forsee issues, but others might spot something. ;)

PS: Out of curiousity, can you read and write okay to the target from 17.04 linking that way? There are no permissions problems? If there is, I'd suggest using the fstab method and changing permissions if you need to as wouldn't recommend changing permissions on a system mounted drive. 

Also, if fstab method, you have ability to stop the partition from automounting, or mounting at all, if you want/need (use # in front of the line in fstab file).

---

### Post by joseph123321123 on 2017-05-29
Ah, 16.10 is dev/sda6. I should have mentioned that.

So at the moment it's an Ok way to open the folders from 16.10, I'm kinda happy with it though I would like to be able to actually open the folders from the left panel in nautilus and also from right-clicking on 'files' in the launcher. Would that be possible through editing the fstab?

I'm going to try this now
> 
[COLOR=#000000]Code:
# /dev/sda6 16.10
UUID=e6a6e484-e99c-4f85-a370-0c640b5b1e76   /media/storage    ext4    errors=remount-ro       0       1[/COLOR]
[COLOR=#000000]You could call /media/storage whatever you like, you need to create that mountpoint, preferably in /media or /mnt. You can call it what you like (/mnt/16.10?). [/COLOR]

[COLOR=#000000]Then, your symlink would look something like:[/COLOR]

[COLOR=#000000]Code:
ln -s /media/storage/Documents /home/joseph/Documents[/COLOR]


---

### Post by Bucky Ball on 2017-05-29
I have edited my last post. You might want to have another quick read. Sorry about that, had some corrections and afterthoughts, hit save then saw your post. Sounds like you've got the gist though and those links you've created are working. Yes, try that keeping an eye on the paths. As mentioned, generally /mnt is used. I'll have a quick look at the diff.

Yea, use /mnt. In other words:

```
# /dev/sda6 16.10
UUID=e6a6e484-e99c-4f85-a370-0c640b5b1e76   /mnt/storage    ext4    errors=remount-ro       0       1
```

```
ln -s /mnt/storage/Documents /home/joseph/Documents
```

For nano, read down the bottom of the terminal: 'control+x' then 'y' (from memory, but don't think about it anymore! Sad. ;)).

---

### Post by joseph123321123 on 2017-05-29
Ok, So I edited the fstab with nano and added the lines that you suggested. Seems logical to call it storage.

[COLOR=#000000]*Code:*[/COLOR]
[COLOR=#000000]*# /dev/sda6 16.10*[/COLOR]
[COLOR=#000000][I]UUID=e6a6e484-e99c-4f85-a370-0c640b5b1e76 /media/storage ext4 errors=remount-ro 0 1

[/I][/COLOR]> [COLOR=#000000]*you need to create that mountpoint, preferably in /media or /mnt. You can call it what you like (/mnt/16.10?). *[/COLOR] I don't really know how to create a mountpoint. Should I have done that before adding the lines to the fstab?[COLOR=#000000][/COLOR]

---

### Post by Bucky Ball on 2017-05-29
Ok. Go back and change the fstab file. Sorry. Was hoping you caught my last. Replace the two instances of /media with /mnt. Just had a check and that is the one, not /media. That is used by the system for removable media. See my last post for the exact fstab line.

Yes, you need that mountpoint:

```
sudo mkdir /mnt/storage
```

That will be reflected in your fstab and will be where your 16.10 partition will be mounted when you boot 17.04 ... hopefully. :)

---

### Post by joseph123321123 on 2017-05-29
The only folder that I can't access from 16.10 in 17.04 is the root.

I still don't really know how to create the mount point. I added the lines to fstab but the file paths are still the same. 

The file path for sda6 is '/media/joe/e6a6e484-e99c-4f85-a370-0c640b5b1e76' 

Is it possible for me to open the folder from the left panel in nautilus if I edit the symlinks?

lol sorry I keep writing posts and then I see that you've posted a reply.

So I did '[COLOR=#000000][FONT=&quot]sudo mkdir /mnt/storage' [/FONT][/COLOR] then I edited the fstab it is now 

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda7 during installation
UUID=13cf7101-a1b7-40c3-ae3f-01db6bb5fca1 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=8ae77fdd-15a3-43e7-8508-8c7aa0acefc4 none            swap    sw           $
# /dev/sda6 16.10
UUID=e6a6e484-e99c-4f85-a370-0c640b5b1e76   /mnt/storage    ext4    errors=remount-ro       0       1
```

---

### Post by Dennis N on 2017-05-29
From your post #7:
> The thing is the symlinks aren't in the home folder.The home folder has the 17.10 desktop, documents, downloads etc, however no symlinks. Damn!

The reason for this is a symbolic link created in folder X can't have the same name as an existing file or folder also in folder X.

You will have to delete the Documents folder in your home folder _before_ you can create a link named "Documents" to your 2nd Documents folder. Or, you can keep the original Documents folder if you give the link another name.

Rather than symbolic links, my practice is to just make some bookmarks in the File Manager to key locations in my data folder (which is on another partition). The bookmarks show up in the side pane.

---

### Post by joseph123321123 on 2017-05-29
Hi Dennis,

Thanks for your reply. I think i'm going to go with bookmarks for now.

Cheers

---

### Post by Dennis N on 2017-05-29
> **joseph123321123 said:**
> Hi Dennis,

Thanks for your reply. I think i'm going to go with bookmarks for now.

Cheers

Good decision - I assume your new fstab mount entry in post #14 is working o.k?

---

### Post by Bucky Ball on 2017-05-29
For what it's worth, you're one step away. Your symlink command should now look like this, which was given in a previous post in a description of this from start to finish.

Delete the original /Documents folder in the 17.04 /home and create the symlink:

```
ln -s /mnt/storage/Documents /home/joseph/Documents
```

You're done.

Oh, well. You almost got there. A matter of revising and nutting it out. All the information is here and elsewhere. You can find out how to create a directory in Linux in no time online, but you'll find it somewhere here. :) Good luck however you go; symlinks, bookmarks or whatever.

(Never had the issue of duplicate folders with a symlink and an actual directory from memory. One is a folder, one is symlink, so they are not duplicates, but will give that a try later and confirm. I've used these for ages and can't recall that issue.)

---

### Post by joseph123321123 on 2017-05-30
Ok, So Bucky I went with what you suggested in your previous post, I deleted the originals and made new symlinks and it worked!!

I was really pleased. I also found the folder icons in '/usr/share/icons/Humanity/places/48' and swapped them so that it looked as it would without the arrows.

....So i thought ok i'll reboot to make sure it's all ok. Now my the folders are missing from my home folder. I've added a screenshot [https://ibb.co/fDjY0v](https://ibb.co/fDjY0v)

Also it appears that my 16.10 partition isn't mounted though GParted shows it's mount point [https://ibb.co/dKACtF](https://ibb.co/dKACtF) What I mean is it isn't in the launcher or in other locations in nautilus.

I'm going to have a look at the fstab entry now. Any ideas what the problem is guys?

EDIT I looked at the fstab, it's still as it was in post #14.

---

### Post by Dennis N on 2017-05-30
> **joseph123321123 said:**
> Also it appears that my 16.10 partition isn't mounted though GParted shows it's mount point [https://ibb.co/dKACtF](https://ibb.co/dKACtF) What I mean is it isn't in the launcher or in other locations in nautilus. I'm going to have a look at the fstab entry now. Any ideas what the problem is guys? EDIT I looked at the fstab, it's still as it was in post #14.

Partitions mounted in fstab won't show in the sidebar. File Manager sidebar only shows unmounted partitons and partitions that have been mounted from the file manager. 

To access partitions mounted in fstab, you either browse to the desired location through the symbolic link (or the mount point), or else create bookmarks in the sidebar to quickly get to a location on the partition. As I said previously, I skip the symbolic links and use bookmarks. 

Technically, a mount by clicking on file manager device icon mounts the partition using udisks2, which always creates mount point /media/username/xxxxx.

---

### Post by joseph123321123 on 2017-05-30
Ok thanks Dennis.

The main thing problem I have now is that I can't actually access the sda6 partition. I think it mgiht be mounted, though it doesn't appear in the launcher. If it isn't could I mount it in terminal?

I tried '/mnt/storage'

and it just said 'bash: /mnt/storage: Is a directory'

---

### Post by Dennis N on 2017-05-30
gparted shows it as mounted at /mnt/storage, so it is mounted. Unity's launcher on the left probably won't show partitions mounted in fstab just like Files doesn't. I haven't got Unity any more, but that is my recollection (I now have Ubuntu Gnome, and it's launcher (dash) doesn't show partitions at all.)

Just click on one of the symbolic links you created in your home partition, and you should open the target folder in your sda6 partiton.

---

### Post by Dennis N on 2017-05-30
This may help: The root (/) of the file system on sda6 is the folder /mnt/storage. So if you want to get to the root, just open that folder.

---

### Post by joseph123321123 on 2017-05-30
Sorry I don't really understand. How do I open /mnt/storage of sda6?

---

### Post by joseph123321123 on 2017-05-30
If I open sda7 it won't let me open the root folder. [https://ibb.co/d1LTYF](https://ibb.co/d1LTYF)
Though did you mean the root of sda6? I can't access sda6 at the moment.

Ps. you'll notice the layout of the left panel, ill post about that in a moment

---

### Post by joseph123321123 on 2017-05-30
So I thought as the sda6 partition appeared in the launcher before and as you mentioned how > Unity's launcher on the left probably won't show partitions mounted in fstab just like Files doesn't. I would remove the lines from fstab, add bookmarks and see if that would work. I copied the lines to a text document so that I could easily paste them in again.

 Yesterday I made bookmarks from the sda6 partition and that was all good, though I didn't reboot to make sure. I think if I had done I might have got the problem I now have which is that after rebooting the bookmarks give a message as 'unable to find the requested file' [https://ibb.co/iu87tF](https://ibb.co/iu87tF)

I also renamed the folder that I tried it with this time so 'Music' on sda6 is now called 'Music2' I named it as that as I wanted to be sure that there weren't any problems with the two folders having the same name when I tested to see if it worked after rebooting. However what I have now is what is shown in the picture.

You'll see that the layout is kinda messy and that the originals aren't there. I'm thinking it would probably be quite easy to get originals in the home folder again, or possibly not actually have the originals as i'd be saving to the sda6 partition. However I now have the problem with the bookmarks.
 
If I could reboot and be able to open bookmarks from the sda6 partition then that would pretty much solve it and maybe the left panel in nautilus could be tweaked so that it was tidy.

 I thought maybe adding the lines to the fstab again might be what I should be doing so I did that, however when I try that the sda6 partition disappears from the launcher. Should I maybe be doing something else with the fstab file also?

EDIT Also I just tried this. So I made a music folder in the home folder and then I made a symlink of 'Music' from sda6 in the new music folder then I rebooted but the symlink looks like a text file and not a folder and when I try to open it it says
'the link 'musc' is broken and cannot be used as it's target '/media/joe/e6a6e484-e99c-4f85-a370-0c640b5b1e76/home/joe/Music' doesn't exist'.
The folder is there however though it appears the symlink isn't working after rebooting :/

---

### Post by Dennis N on 2017-05-30
> **joseph123321123 said:**
> Sorry I don't really understand. How do I open /mnt/storage of sda6?

So you are using Files (Nautilus) as the file-manager (same as Ubuntu Gnome uses).

Open Files > open "Other Locations" (at bottom of sidebar) > open "Computer" > open **mnt** > open **storage**.

You are now at root of sda6. I also suggest you bookmark this so you can get there in one click.

---

### Post by joseph123321123 on 2017-05-30
Ah it's there in 'Other Locations' if the lines aren't in the fstab, though if I add the lines then it doesn't appear.

---

### Post by Dennis N on 2017-05-30
The last post is a little confusing. but if you remove the lines from fstab, you are back where you started and the sda6 is not mounted on startup.  So the bookmarks won't work because there is no path to the bookmarked folder - the path has to go through the mounted mount point. If you want to use either symbolic links or bookmarks, you need to mount the partition before either works. If you change the way you mount sda6 - like from the file manager side pane - they won't work anymore, because mounting that way uses a different mount point, and the bookmark expects the the path to use the original mount point /mnt/storage.

---

### Post by joseph123321123 on 2017-05-30
Sorry for the post being confusing. The picture is from today not yesterday.

> [COLOR=#000000]So the bookmarks won't work because there is no path to the bookmarked folder - the path has to go through the mounted mount point. If you want to use either symbolic links or bookmarks, you need to mount the partition before either works.[/COLOR]

I had sort of assumed that might be the case. I have been trying it without the edited fstab as once I add the lines the partition is no longer visible in 'Other 'Locations'.

I'm fairly sure it was visible in 'Other Locations' yesterday with the new lines in the fstab.

So if I was able to add the two lines to the fstab and the sda6 partition was still there in 'Other Locations' then I could make bookmarks and I guess that would then work after rebooting. 
The thing is if I add the lines now it disappears. Do I need to edit it again maybe?

---

### Post by Dennis N on 2017-05-30
> **joseph123321123 said:**
> Ah it's there in 'Other Locations' if the lines aren't in the fstab, though if I add the lines then it doesn't appear.

Right. If you have a partition mounted in fstab, it is not shown on "Other Locations"  as a partition, so you have to go through "Computer" and down to **mnt** folder to get to it as I described, and then you are on the sda6 partition! 

But once you navigate to a desired location, make a bookmark so you don't need to repeat this.

The symbolic links should be working too. Don't they?

---

### Post by joseph123321123 on 2017-05-30
Ok the /mnt/storage is empty though I think that might be as it is mounted through the file manager as you mentioned. I'm going to reboot and see if it is in the mnt folder. Thanks

EDIT It is!

---

### Post by joseph123321123 on 2017-05-30
Ok great!!!

So I now have bookmarks in the left panel in nautilus with file paths such 'mnt/storage/home/joe/Documents' etc. [https://ibb.co/mP8kxa](https://ibb.co/mP8kxa)
Thank you so much!

I guess I could now make Documents. Downloads etc. folders in the home folder although I'm happy with the way it is at moment.
I'm going to make sure that a few things are working as they were before and when I've done that i'll mark it as solved!
Thanks again! :P

---

### Post by Dennis N on 2017-05-30
> **joseph123321123 said:**
> Ok great!!!

So I now have bookmarks in the left panel in nautilus with file paths such 'mnt/storage/home/joe/Documents' etc. 

Looks good. I'm glad all the details are cleared up. What you show is exactly the way I do it on my own system.

---

