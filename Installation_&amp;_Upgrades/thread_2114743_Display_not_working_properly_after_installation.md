---
title: "Display not working properly after installation"
date: 2013-02-10
forum: Installation &amp; Upgrades
---

### Post by sitek8 on 2013-02-10
Hello,

I saw a lifehacker post about turning an old desktop into a NAS with Ubuntu (which I've wanted to do for a while) and decided to give it a try. I've installed Ubuntu on multiple computers before with little to no issues. This time, after the installation (12.04), it would boot to a black screen, which I had seen posts for and fixed that issue. Now when it boots to the desktop, it's hard to explain so I took a picture. 
[IMG]http://imgur.com/9Ey6HMx[/IMG]
If i boot to the liveCD it works fine, but when I boot to the installation, this is what I get. I'm going to try and do the installation again overnight while downloading the updates to see if it makes a difference. Any help would be appreciated. Thanks

---

### Post by oldfred on 2013-02-10
Welcome to the forums.

I have the same issue both with liveCD and first boot after install with my nVidia 9600GT.

       To install Ubuntu, boot from the cd press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option.
USB boot - At the menu press tab on the first option to edit the boot options and replaced the 'splash' option with 'nomodeset'. 
then
On first boot after install, press e on getting the GRUB bootloader menu. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode), install nVidia driver suggested my Ubuntu

    
If not nVidia nomodeset may work but there are other boot parameters also.

       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by sitek8 on 2013-02-11
I figured it out...when the screen got all funky like that, I hit ctrl+alt+delete and waited for the login screen, then took it off 3D and it works perfectly. I did what you posted just to be sure. Now I have everything installed, drives mounted, but I can't see the Ubuntu drive on my Windows PCs. I followed multiple posts on multiple forums about how to share between the two and my Windows computers on the homegroup seems to be working fine together, but I can't see the Ubuntu drive. Any ideas?

---

### Post by oldfred on 2013-02-13
Best to start a new thread on Samba and your Ubuntu & Windows Samba configurations. I have not used Samba since I converted Laptop to Ubuntu and use NFS to copy data between systems.

---

### Post by MAFoElffen on 2013-02-13
> **sitek8 said:**
> I figured it out...when the screen got all funky like that, I hit ctrl+alt+delete and waited for the login screen, then took it off 3D and it works perfectly. I did what you posted just to be sure. Now I have everything installed, drives mounted, but I can't see the Ubuntu drive on my Windows PCs. I followed multiple posts on multiple forums about how to share between the two and my Windows computers on the homegroup seems to be working fine together, but I can't see the Ubuntu drive. Any ideas?

Easy- Install Samba on your Ubuntu.
Start gedit:
```

sudo gedit /etc/samba/smb.conf

```
Edit the following key/value pairs in the [global] section of /etc/samba/smb.conf:
```

   workgroup = WORKGROUP
   ...
   security = user

```
Create a new section at the bottom of the file for the directory to be shared:
```

[share]
    comment = Ubuntu File Server Share for Documents directory
    path = /home/user_name/Documents/
    browsable = yes
    guest ok = yes
    read only = no
    create mask = 0755

```
That would smb share a user's home directory's Document directory of a user called "user_name"...

Then shutdown and restart Samba to pick up the changes:
```

sudo restart smbd
sudo restart nmbd

```
You should now be able to see the Win Workgroup from your Ubuntu PC. If you don't see them, but can see then from the win PC's, go to the WIn boxes and allow that box through their firewalls. Helps if you use a static IP... But not required. Win Workgroup should see the Ubuntu box on Workgroup, Network mapped drives.

Hope that helps.

---

