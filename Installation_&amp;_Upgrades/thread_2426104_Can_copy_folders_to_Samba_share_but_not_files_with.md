---
title: "Can copy folders to Samba share but not files within Error Operation Not supported"
date: 2019-09-04
forum: Installation &amp; Upgrades
---

### Post by fozziebear on 2019-09-04
I have a really strange situation when trying to copy directories and files between two Ubuntu based machines. 
***PC One (***Lubuntu 19.04) has files and folders being transferred. ***PC Two ***has Xubuntu 18.04 with samba share receiving files and folders.

On*** PC Two*** I installed Samba from the Ubuntu Repositories using ***Sudo get-apt Install samba.*** I then created a directory to share using **mkdir /home/john/shared. **I then edited the** smb.conf **file and changed the workgroup to match both machines and added the following to the end of the file

[shared]
path = /home/john/shared
valid users = john
read only = no

I then changed ownership ***[COLOR=#333333][FONT=UbuntuMono]sudo chown john /home/john/shared. [/FONT][/COLOR]***After a reboot of ***PC Two*** I could then see the shared folder "shared" from ***PC One*** (Lubuntu). However when I tried to copy a folder with a number of files from ***PC One*** to ***PC Two*** share I got the error message ***Error Operation Not Supported .***
 At first I thought nothing had copied but when I refreshed the view I could see that the folder had copied across but was empty of files. To test permissions If I right clicked on the share I could create a new folder or text file. I then tried to copy and past some individual files into the previously created folder and they copied successfully. 
I found further information about changing permissions so tried **sudo chown -R john /home/john/shared** to pass down ownership to child files and folders? However the situation is still the same and I cannot copy a folder with all its contents from one PC to another. For further info both installations have the same username and password

I would appreciate any suggestions

---

### Post by TheFu on 2019-09-04
File sharing between Unix systems is best handled using NFS which honors the expected file and directory permissions.
I won't attempt to help with Samba, since things have changed so much but if you are interested in NFS, I'm happy to help or you can search "ubuntu nfs" to find a guide.
[https://help.ubuntu.com/lts/serverguide/network-file-system.html](https://help.ubuntu.com/lts/serverguide/network-file-system.html) is the official version.

NFS configuration is 1 file on the server and 1 line in the fstab on the client.  Both the client and the server should have static IPs. That will make things easier.

---

### Post by fozziebear on 2019-09-06
> **TheFu said:**
> File sharing between Unix systems is best handled using NFS which honors the expected file and directory permissions.
I won't attempt to help with Samba, since things have changed so much but if you are interested in NFS, I'm happy to help or you can search "ubuntu nfs" to find a guide.
[https://help.ubuntu.com/lts/serverguide/network-file-system.html](https://help.ubuntu.com/lts/serverguide/network-file-system.html) is the official version.

NFS configuration is 1 file on the server and 1 line in the fstab on the client.  Both the client and the server should have static IPs. That will make things easier.

Sorry for delay in responding. I did create a reply yesterday but it obviously didn't post.!!!
Many thanks for your very kind offer but I don't think NFS is the ideal solution and I'd rather try and fix Samba. 

This is really a one off exercise with the two Ubuntu based machines as I am just upgrading my ***Download PC ***(PC Two Xubuntu 18.04 as I use ***get_iplayer ***to record plays and TV programmes on the BBC) to a better system spec and trying to transfer the several hundred gigabytes of files over from one to the other. I could use an external USB hard drive but I don't have a drive big enough and its so slow with only USB 2.0. 

I also have a mainly windows network and I use Samba to share files between the Linux machine and my PCs and Android boxes on the network which Samba is common to.  I just wanted to transfer files over the Gigabit lan connection preferably overnight.

I am not sure what the issue is whether its ownership or permissions. I have now tried setting a 777 mask which I found on one website but even that fails. Perhaps the smb.conf file needs further instructions?
Thanks again
Fozzie

---

### Post by TheFu on 2019-09-06
For copying lots and lots of files, I use rsync.  That works over ssh, so ssh needs to work between the systems. If the copy gets interrupted, just restart the same rsync command again and only files not previously transferred, or ones that have been updated, get transferred again.  Samba would be faster, but rsync is just so much more convenient.  

After the rsync finishes, delete the files on the source, assuming it isn't your backup.

---

