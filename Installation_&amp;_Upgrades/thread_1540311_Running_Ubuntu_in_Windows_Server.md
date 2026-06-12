---
title: "Running Ubuntu in Windows Server"
date: 2010-07-27
forum: Installation &amp; Upgrades
---

### Post by neomaximus2k on 2010-07-27
I have a weird question, I need to run ubuntu under windows server 2008.

The reason is I need to create a replica of our online server for development purposes, so the idea is to have a version of ubuntu server running as a service under windows server 2008, this would then allow apache mysql and php to be run within ubuntu.

So how would I go about doing that, it would also need to gain access to files on a secondary drive which is ntfs.

---

### Post by kevinatkins on 2010-07-27
Having Ubuntu Server running as a 'service' under Windows Server 2008 wouldn't be feasable. What you could try is virtualisation.
I use Virtualbox on an Ubuntu host, but Windows versions are available - go to [http://www.virtualbox.org/]("http://www.virtualbox.org/")
Virtualbox works really well, is Open Source, and should do just what you want.

---

### Post by neomaximus2k on 2010-07-27
I need to ensure it runs as soon as the server is turned on hence the service so a user doesn't need to login can this be done with virtualisation?

---

### Post by neomaximus2k on 2010-07-27
So far the only solution I have found is VMWare Server which will allow a virtual machine to be run at system startup, any other solutions?

---

### Post by kevinatkins on 2010-07-27
OK yes, I see your issue. Indeed, I don't think there is a way currently to have Virtualbox run a virtual machine on host startup (or for that matter, to shut said VM down gracefully on host shutdown) and indeed, VMWare did accommodate this when I last tried. You could use VMWare but I don't know about licensing issues re. commercial application.
The other alternative might be to install Apache, MySQL and PHP directly on your Windows server - there's a convenient means of doing this using XAMPP which rolls everything together for you... There are one or two potential 'gotchas' but nothing insurmountable from my own personal experience of doing this. Of course, if you've already got, say, MS IIS running on your host server, you might need to adjust ports etc but it might be worth looking into if all else fails. Good luck!!

---

### Post by neomaximus2k on 2010-07-28
Thanks Kevin, well as Linux distro's are open source there shouldn't be a licensing issue regarding running Linux as a secondary OS from within windows itself.

Sadly with XAMP the configuration of the paths would be totally different of that compared to Unix and would require to many changes to the script just to work around it, as the script I work on is an on-line application with over 800 files it would be a nightmare :(

---

