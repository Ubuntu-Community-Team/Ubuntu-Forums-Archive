---
title: "How to regain access to newly added partition to fstab?"
date: 2018-09-20
forum: MINT
---

### Post by drpeppercan on 2018-09-20
[SIZE=1]Specs: Linux Mint / Tara (Cinnamon).[/SIZE]
After I add a new partition to my fstab file, take ownership, and add permissions, it goes away!
Before doing it, the partition was mounting and showing on its own in the Files window, left panel under Devices. Except root was the owner, reason why I couldn't use it.
So, now that I did all this to be able to use it, it just goes away. I recall I used to be able to recall it using [Disk Indicator]("http://www.teejeetech.in/2017/01/disk-indicator-v171.html"). But when trying to install it's PPA, it told me: *Unable to locate package indicator-diskman*
And the link for its .deb file is broken :(

These are the steps I follow to gain ownership of the partition (thanks mostly to oldfred):




[SIZE=3]**Install Steam in an external partition in a separate drive**[/SIZE] - 



[LIST]
[*]Find the partitions IDs -
[/LIST]
sudo blkid -c /dev/null -o list

The ID will look similar to this: 2bacbf62-7a77-4ab4-8b25-063e52381eaf. It is needed later.


[LIST]
[*]What's mounted?
[/LIST]
ls -al /mnt/

- Should you want to use a mounting point existing already, then you'll see it now. 




[LIST]
[*]For this example though, we'll create a new one. See below.
[/LIST]
Create the mounting point

sudo mkdir /mnt/steam-files




[LIST]
[*]Once created, we'll mount it:
[/LIST]
sudo mount /dev/sda5 /mnt/steam-files




[LIST]
[*]Now see its contents: 
sudo ls -al /mnt/steam-files.
[/LIST]



[LIST]
[*]Then we UN-mount what we manually mounted:
[/LIST]
sudo umount /dev/sda5



And finally now we make the mount in the file system table. 
It is SOP to always make a backup of any file that one edits . always .. never can tell what might perchance - cheap insurance: 

sudo cp /etc/fstab /etc/fstab-10Oct2016



And now we can fire up a favorite text editor - gedit as my reference for the editor :

sudo -H gedit /etc/fstab



Which opens the file with the elevated privileges to edit a system file. 
Now add these 2 lines at the bottom: 
#mountpoint for sda5 steam-files added 10Oct2016 
UUID=2bacbf62-7a77-4ab4-8b25-063e52381eaf /mnt/steam-files            ext4    defaults        0       2



As you can see, "sda5 steam-files added 10Oct2016 UUID=2bacbf62-7a77-4ab4-8b25-063e52381eaf" is all taken from the results from #1 above. 


[LIST]
[*]Save changes. Ignore errors that might show in Terminal, like this one:
[/LIST]
(gedit:10332): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files




[LIST]
[*]Now, have the system check the file for errors, reload /etc/fstab:
[/LIST]
sudo mount -a




[LIST]
[*]Finally we make "YOU" the owner of that partition AND ALL the files contained in that partition- per your request . now that may not make steam happy. Depending on your use case steam may want ownership ???? 
sudo chown -R javier:javier /mnt/steam-files
[/LIST]
reboot the system ! 
See the results of your efforts: 
booted from sdb:


[LIST]
[*]ls -al /mnt/steam-files
[/LIST]
verifies that YOU - javier - have access to that file system. /mnt/steam-files is your oyster to do with as YOU want.[COLOR=#000000][FONT=&amp]

[COLOR=windowtext][COLOR=windowtext][FONT=Calibri]
Thread [/FONT][/COLOR][[FONT=Calibri]Source[/FONT]]("https://ubuntuforums.org/showthread.php?t=2339524")[/COLOR]

[/FONT][/COLOR]

---

### Post by TheFu on 2018-09-20
Did you create a file system on the partition using **mkfs**?  If not, you need to do that.

Almost all config files in Linux use tabs and spaces as delimiters.   "stream{space}files" makes 2 separate fields. Either quote the entire path or don't use spaces (or other special characters) in the path.

The example mount point of "/mnt/steam files" is a terrible choice for use inside the fstab.
Mounting permanent storage anywhere under /mnt/ is poor because that area is for temporary mount locations for root doing work.  The first **mount** command that used /mnt is 100% fine.  That is the purpose for /mnt, but when it is used inside the fstab, that's a failure, IMHO.

---

### Post by drpeppercan on 2018-09-20
> [COLOR=#000000]Did you create a file system on the partition using [/COLOR]**mkfs? If not, you need to do that.**
I can't say I did. I used Gparted to resize (shrink) a larger partition, then made the new smaller partition with the remainder. I chose ext4, but that's all I did.

> [COLOR=#000000]The example mount point of "/mnt/steam files" is a terrible choice for use inside the fstab.[/COLOR]
I couldn't agree more. It must have been a typo. It didn't affect my coding because I was using a different name: steam-lib. Thanks for catching it though. I corrected my personal documentation.

> [COLOR=#000000]Mounting permanent storage anywhere under /mnt/ is poor ...[/COLOR]
That's good to know!
Then if not there, where?

Thanks

---

### Post by TheFu on 2018-09-20
Different areas are made for different mounts. The FHS spells out what each area is for. google it. If you follow that or stay outside those directories, it is fine.  The short answer is ... 
don't use:
* /mnt (only for temporary use)
* /media (anywhere; other system tools manage this area, so avoid conflicts)
* /home/{userid}/   (mounting under some user's home brings other complications)

Pretty much any empty directory anywhere else can work. There are different opinions about this. The "mount point" must exist already. Don't bother changing permissions until AFTER the storage is mounted there.

If you are stuck, show lsblk, df -hT, and ls -al /path/to/mount-before-mounted,  spell out which LV or partition you want mounted and the contents of /etc/fstab.

---

### Post by ajgreeny on 2018-09-20
*Thread moved to **MINT**.* which is more appropriate and a better fit for your OS.

---

