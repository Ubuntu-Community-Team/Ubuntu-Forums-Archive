---
title: "Sharing folders between two Ubuntu Machines"
date: 2005-08-06
forum: Installation &amp; Upgrades
---

### Post by exphiles on 2005-08-06
Ok, this is the first time I got two computers with Ubuntu installed on each. I normally have 1 linux machine and the others are Windows. Now, I know how to share folders and printers between Windows and Linux. But (I know this might be a dumb question), how do I share folders and printers between two Ubuntu machines?

Do I still use SMB or is there another way of sharing folders and files between two linux computers? If so, how do I set it up?

Also, how about my printer? My printer prints perfectly on the Ubuntu machine (assume IP is 192.168.0.1) where it is connected directly. How do I print from another computer (Ip is 192.168.0.2)?

Do I use SMB? CUPS? LPD? How do I configure it?

Thanks in Advance

---

### Post by FLeiXiuS on 2005-08-06
The fastest and easiest way to share files between two or more linux systems is to use NFS.  NFS is by far the fastests / best, IMO.

Documentations including configuring and setting up can be found here.

[http://www.tldp.org/HOWTO/NFS-HOWTO/](http://www.tldp.org/HOWTO/NFS-HOWTO/)

I would've posted a really long how-to for this subject.  But I encourage users to read from other sources.  :-)  If you have any questions about anything stated above, please repond and I would respectively respond to your response.

---

### Post by az on 2005-08-06
Hey Flex, what about the shared folders GUI?  

I click on it and it tells me to share folders I have to install Samba or NFS.

So I install Samba and the I can share files without editing text files.  

I borked up my network and started over, this time I implemented NFS (I installed nfs-common and nfs-kernel-server) and could not get it to work out-of-the-box.  I went back and installed samba (which I had removed) and got to share files again. Any ideas what needs to be done other than using the shared folders GUI in Ubuntu to get NFS to go?

---

### Post by lonetree on 2005-08-09
Wonder any of you have this problem. I have a mixture of linux (ubuntu, novell suse) and windows machines in my home network, have a simple NAS call a LANDISK ([http://www.vgear.com)](http://www.vgear.com)), acting as a file server.

My problem:

I have problem in date and time when copying folders and files from :

i) linux to linux (i.e ubuntu to suse, suse to ubuntu) - time and date of files
always get changed to 1980 01 01 Tues 0800am GMT despite the original
date as something else.

ii) linux to windows (i.e suse to windows or ubuntu to windows) - time and date
always get changed to a few hours ahead of the current time of the copying
process, despite the original date as something else.

iii) linux to NAS - the time and date always get changed to 1980 01 01 Tues
0800am GMT (when the network folder is not mounted) and time and date
get changed to current time and date of the copying process (when it is
being mounted as a share folder, ie /media/share-folder)

Wierd isn't it? Am I doing anything wrong here or what?

Have been posted in quite a number of threads and still no one has reply. Hopefully someone can see this and reply, a yes or no will be at least an answer to me.

Thanks in advance.

Regards,

---

### Post by nocturn on 2005-08-10
[QUOTE=azz]Hey Flex, what about the shared folders GUI?  

I click on it and it tells me to share folders I have to install Samba or NFS.

So I install Samba and the I can share files without editing text files.  

I borked up my network and started over, this time I implemented NFS (I installed nfs-common and nfs-kernel-server) and could not get it to work out-of-the-box.  I went back and installed samba (which I had removed) and got to share files again. Any ideas what needs to be done other than using the shared folders GUI in Ubuntu to get NFS to go?[/QUOTE]

install portmap (if you haven't done so).
set up /etc/exports like this:
/sharedfolder      machinewithaccess(rw)

restart nfs

On the client, do 
mount sharingserver:/sharedfolder /mountpoint

That should do it.

---

### Post by mohsin on 2005-08-13
i installed samba successfully .. but cant able to share folders it gives error permission not seted :( .. 

 what i should do now

---

### Post by lonetree on 2005-08-13
[QUOTE=mohsin]i installed samba successfully .. but cant able to share folders it gives error permission not seted :( .. 

 what i should do now[/QUOTE]

Did you set your workgroup correctly? The default workgroup name should be mshome. Try checking your workgroup name.

Hope I am right.

regards,

---

### Post by mohsin on 2005-08-13
yupz .. its mshome hmmmm folders shared thnx bro but 

 it gives error that cant open or cant read abc folder deleted or permission is not allowd 

  :---)

---

### Post by lonetree on 2005-08-14
[QUOTE=mohsin]yupz .. its mshome hmmmm folders shared thnx bro but 

 it gives error that cant open or cant read abc folder deleted or permission is not allowd 

  :---)[/QUOTE]

Have you added the network user?

Do this test, if you have not already added your network user. Goto **Places | Network Servers | **, then at the address field, key in "smb://ip address (of your sahred machine) /shared folder name/"

See if you are able to see the shared files.

Regards,

---

