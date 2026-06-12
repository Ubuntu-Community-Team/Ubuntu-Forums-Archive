---
title: "More disk space, virtual Win XP on VMware workstation"
date: 2006-05-30
forum: Installation &amp; Upgrades
---

### Post by ampop on 2006-05-30
I installed a virtual Win XP on VMware workstation. I just give 2GB to the virtual win XP. It's possible give more space, or I must reinstall the virtual Win XP?

Thank you.

---

### Post by ampop on 2006-05-30
Any Ideias please?
](*,)

---

### Post by st4rdr1ft3r on 2006-05-30
You could add a second hard-disk. I'm not sure if you can resize the main one or not.

---

### Post by ayates on 2006-05-30
There's a utilty called vmware-vdiskmanager which will expand it on the host.

The caveat is that you need a 3rd party partitioning tool for the XP machine to expand it there.

---

### Post by ampop on 2006-06-01
[QUOTE=ayates]There's a utilty called vmware-vdiskmanager which will expand it on the host.

The caveat is that you need a 3rd party partitioning tool for the XP machine to expand it there.[/QUOTE]

That's it. Thank you very much.

---

### Post by tim-e on 2006-08-23
Awesomeness.  Thanks for the info!


I battled with Debian 3.0r1 for 3 days to get vmware to work and just couldn't.  10 minutes' time spend with Ubuntu and it's up and running like a charm!


:KS

---

### Post by agentRocky on 2008-02-28
Hi ayates,

I need to expand the disk space on VM but cant the utility vmware-vdiskmanager. I've read plenty of threads and know if i can find this tool i'll be sorted. Can you tell where i could find it?

Sorry if its an obvious answer but i've missed it if it is!
Cheers

---

### Post by pepper_bg on 2008-03-04
It is installed in the same directory where your vmware is installed:
```

iii@iii-desktop1:~$ which vmware
/usr/bin/vmware

iii@iii-desktop1:~$ which vmware-vdiskmanager 
/usr/bin/vmware-vdiskmanager

```

---

### Post by frobroj on 2008-03-15
Note - You don't need a third party partition tool. You can use windows "diskpart". Here is a great howto on the subject. Note if it is a system drive you will need to mount it on a different VM...
[http://www.geekzilla.co.uk/View18A035DE-06FF-4EA6-BC77-57D431CD50DD.htm](http://www.geekzilla.co.uk/View18A035DE-06FF-4EA6-BC77-57D431CD50DD.htm)
Hope that helps!

PS Just performed this and it worked great. One tip that may save some time is  to copy your system vmdk file to another location and extend the new vmdk. Then you can simply add an existing hard disk image to your virtual machine and point it to that file. Then boot and you can start on the diskpart extending piece. This will also preserve your original vmdk file till such time as you complete the extension and replace the file with the new one.

---

