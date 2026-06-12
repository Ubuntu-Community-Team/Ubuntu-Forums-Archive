---
title: "[SOLVED] Wubi vs. standard install"
date: 2008-05-18
forum: Installation &amp; Upgrades
---

### Post by Stolea on 2008-05-18
Which installation is better, Wubi or the standard way?
If I understand it correctly, Wubi will set up Ubuntu on an NTFS drive as part of a normal Windoze install. Does that mean that Ubuntu is not EXT3 dependant?
What are the advantages or disadvantages of this installation?

---

### Post by buntunub on 2008-05-18
Installing via Wubi will give you a large file inside of Windows. I am not sure if that somehow installs via its own filesystem or not, but I dont think so. That being the case then you would have your Wubi system on an NTFS filesystem -- not the greatest way to go. Looking at the docs, it does say that running via Wubi will give you degraded performance from that of a full install. So, the optimal way to go would be to do a full install on a partition or partitions with at least 5 Gig of space for everything. Lots of install guides abound for Ubuntu. My personal pref is to go with extended partitions for /boot, / (root), /home, and /var partitions. Bear in mind that Windows needs to be on the first partition. Also, you can only have up to 4 primary partitions, but a nearly unlimited number of extended partitions. Good luck and have fun learning about your computer and linux!

---

### Post by Stolea on 2008-05-18
Thanks.
I currently have 200gig drive that is a C:\ (WINXP only) and D:\ (Data). I just bought another 320Gig SATA drive that I was going to set up for Ubuntu. I have PQMagic and was going to preformat that drive to 1xEXT3 and the swap drive.
I always like to keep my OS and the data separate. Had too many bad experiences where Windoze trashed itself and took everything with it.
Do you suggest to set up 4 EXT3 partitions and the swap file?

---

### Post by HunterThomson on 2008-05-18
> **Stolea said:**
> Thanks.
I currently have 200gig drive that is a C:\ (WINXP only) and D:\ (Data). I just bought another 320Gig SATA drive that I was going to set up for Ubuntu. I have PQMagic and was going to preformat that drive to 1xEXT3 and the swap drive.
I always like to keep my OS and the data separate. Had too many bad experiences where Windoze trashed itself and took everything with it.
Do you suggest to set up 4 EXT3 partitions and the swap file?

"I" would suggest putting both window$ and ubuntu on the same Master harddrive. Then format the 320 harddrive to Fat32 and use it as a slave drive for both window$ and ubuntu to read. There is also no reason to preformat partitions. You do that in the installer anyway. However, preshrinking the window$ partition would be a good idea. The ubuntu partitions would be best to setup like this

what is left is Window$ about 50GB
150MB /boot ext2
4GB   Swap
20GB  /   (root) ext3
15GB  /home
90GB format fat32

the other harddrive format all fat32

---

### Post by HunterThomson on 2008-05-18
Or if you really want to get nuts. use the remaining 90GB on the Mater harddrive for FreeBSD, Solaris, and BackTrack3 71|Vux. Now that would be cool:guitar:

---

### Post by Stolea on 2008-05-18
I am struggeling with Ubuntu.... I might just cut my Linux teeth on that before I do anything else. Thanks all the same though. :)

---

### Post by Stolea on 2008-05-18
I didn't feel comfortable with mixing Linux and Windoze on the same drive. I  ghosted the windows partition and the windows data drive to the new 320Gig.
I allocated the entire 200gig drive to Ubuntu in the way you suggested just slightly larger partitions plus one /var partition.
It all seems to work OK from what I can tell, which is bugger all at this point.
I tried to mount the NTFS drives, but it won't have any of it. Any idea what I am doing wrong. I need to be able to get to the data on the NTFS drives or this is a total waste of time.
My network and the computers show, but again it won't show any drives on the computers.???

---

### Post by buntunub on 2008-05-18
> **Stolea said:**
> I didn't feel comfortable with mixing Linux and Windoze on the same drive. I  ghosted the windows partition and the windows data drive to the new 320Gig.
I allocated the entire 200gig drive to Ubuntu in the way you suggested just slightly larger partitions plus one /var partition.
It all seems to work OK from what I can tell, which is bugger all at this point.
I tried to mount the NTFS drives, but it won't have any of it. Any idea what I am doing wrong. I need to be able to get to the data on the NTFS drives or this is a total waste of time.
My network and the computers show, but again it won't show any drives on the computers.???

As to your first question, you may need to be root to mount the windows partition. I experienced this as well the first time I did it. Many ways to do this, but I just opened a terminal and typed 

```
$sudo nautilus
```

 That will open nautilus as root. Then I just double clicked on the windows drive and it mounted. You may need to chown it like so - 

```
$sudo chown username /media/windows partition
``` 

(sda1 probably).

As to your second question, you should have no trouble with your windows network out of the box with Ubuntu. You can restart Samba (the windows network protocal) with,

```
$sudo /etc/init.d/samba restart
```

Try that, and then wait a few minutes. The network should sync up np after that and you should be able to open shared folders and such on your windows machine.

---

### Post by Stolea on 2008-05-18
will give it a go shortly. Thanks

---

### Post by Stolea on 2008-05-19
Sorry, but I really am flying blind here. 
How do I get to the command prompt?
where can I tell which SD? the NTFS partions are on?
Eeeeek!
This is soooo embarrasing! I have been working with comuters for 21 years and can do most anything in Dos, OS2, and the multitudes of Windoze, but have absolutely no idea how to navigate in this environment. would I be better off with the kbuntu desktop?

---

### Post by buntunub on 2008-05-19
> **Stolea said:**
> Sorry, but I really am flying blind here. 
How do I get to the command prompt?
where can I tell which SD? the NTFS partions are on?
Eeeeek!
This is soooo embarrasing! I have been working with comuters for 21 years and can do most anything in Dos, OS2, and the multitudes of Windoze, but have absolutely no idea how to navigate in this environment. would I be better off with the kbuntu desktop?

The Terminal is in Applications>Accessories. Before you go there, first to go Places menu and look for your drive there. I suspect its already there and mounted but you didnt look for it. Try finding it there and click on it and you should see it mount on your Desktop, and then just double click it like on windows to open up Nautilus.

---

### Post by Stolea on 2008-05-19
I just clicked on the first of the two NTFS drives and it asked me for my password. Bingo, drive is accessible. and just as an added bonus the second drive turned up on my desktop with a single click.
I am impressed wih the speed images go into thumbnails. I think I am going to like this system.
Next step, The network. If I click on "network servers" I get "windows network", then "IBMPEERS" (Hangover from OS2 days). IBMPEERS lists "Office" and Phils_Laptop".
Clicking on either will result in a blank field.
Any ideas?

---

### Post by iaculallad on 2008-05-19
With regards to your "Blank" windows network: Post the content of your /etc/fstab.

---

### Post by Stolea on 2008-05-19
I assume you mean the files in the directory /etc/fstab. It would appear that this directory does not exist.

---

### Post by iaculallad on 2008-05-19
Type this on your terminal and press enter. Whatever displays, post it here:

sudo gedit /etc/fstab
or
cat /etc/fstab

---

### Post by Stolea on 2008-05-19
Duh! Didn't look for a file! Sometimes geting old sucks.
Here is the text:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=6b2d7a1f-4b9b-438a-905d-22f36f8e1fd6 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=2c102389-64d1-45d2-80e0-d2759043ab4a /boot           ext2    relatime        0       2
# /dev/sda6
UUID=c19dac39-b9e7-4bca-b556-6eb5f562b49d /home           ext3    relatime        0       2
# /dev/sda7
UUID=5c3f8c47-2099-4c6c-8569-5ad36a265946 /var            ext3    relatime        0       2
# /dev/sda9
UUID=7578-7EAE  /windows        vfat    utf8,umask=007,gid=46 0       1
# /dev/sda8
UUID=488c14d4-741a-4408-becd-184d5a6d24ee none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by iaculallad on 2008-05-19
Ok, IBMPEERS was not included in the file: Let's try re-creating it. (Note: Im assuming a static based IP network)

*Let's backup first your fstab file.
sudo cp /etc/fstab /etc/fstab.bak

*Let's make a directory of where we could mount the share.
sudo mkdir /media/ibmpeers

*Open fstab
sudo gedit /etc/fstab

*and include the line below at the very end of your fstab
//192.168.x.x/windows_share_name_from_other_pc /media/ibmpeers cifs user=username,pass=password

*Just replace the 192.168.x.x with the valid IP of the network PC and replace the username and password which you regularly use with the ibmpeers PC.
*This would automount your network share. Hope this could get you on track.

**Or the other way around:**

Go to: Places -> Connect to Server ... (Which will open the "Connect to Server" window)

Service type: Select "Windows share"
Server: this contain the IP number of your ibmpeer
*Afterwhich, click on "connect" button to connect and close the window.
*To get the IP of your ibmpeer, considering its a windows machine type "ipconfig /all" at the command prompt. 
*Close the screen and a Share folder icon will appear on the desktop. Click and view the contents.

---

### Post by pallavis11 on 2008-05-19
See the info below:

[http://a2zhowto](http://a2zhowto) .blogspot.com/

[http://learnphpwithme](http://learnphpwithme) .blogspot.com/

---

### Post by Stolea on 2008-05-19
Ok, followed the steps. Still got no listings
the location field above says "smb://ibmpeers/" It lists the computers on the network correctly.
clicking on the "Office" poduces "smb://office/" but no listing

---

### Post by iaculallad on 2008-05-19
Can you successfully ping the IP Address of ibmpeers? The IP Number of the machine you issued to command ipconfig /all.

---

### Post by Stolea on 2008-05-19
Yep, 192.168.0.2
pings just fine

---

### Post by iaculallad on 2008-05-19
Do try looking at this [page]("https://help.ubuntu.com/community/SettingUpSamba") for detailed information regarding file/folder sharing b/w Ubuntu and windows. Hope this could help.

---

### Post by Stolea on 2008-05-19
will have a read tonight. Thanks for the help. Much appretiated and very generous.

---

