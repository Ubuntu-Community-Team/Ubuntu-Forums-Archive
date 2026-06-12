---
title: "Migrate from desktop to server"
date: 2007-09-06
forum: Installation &amp; Upgrades
---

### Post by jtholt on 2007-09-06
I installed ubuntu desktop after some tome i decided server was the way to go     I have alot of things that i dont want to loose. is there a way to change from desktop to server without losing everything  i have a server disk. i need network boot and the whole bit. please let me know John

---

### Post by zvacet on 2007-09-06
If you have separate home partition you can put your files there,and they will be safe.If you don´t have separate home try this

[http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")

After that you can install server from CD to your previous Ubuntu partition.Keep home unformated.

Second solution may be to install LAMP from synaptic.Synaptic>edit<mark packages by task.

---

### Post by jtholt on 2007-09-10
I would like to install LAMP without reinstalling the whole system. Can you please give me more detailed instructions on how to do so as i am new. Also will LAMP allow network boot/login clients, that is something i relly need. If someone could tell me how to get network boot and login (just like the server)  running that would be great. Thanks for your help  J

PS I dont want to reinstall the whole system if I can help it. Thanks for the help

---

### Post by Anteaus on 2007-09-10
LAMP will not give you network boot capability. 

LAMP (Linux, Apache, MySQL, php) is for serving websites, not to be confused with the fileserver role, which is probably what you want. For a fileserver serving mixed clients your main requirement is Samba, which is relatively straightforward to install  and config, there should be no need at all to start over for this. 

As for network booting, better to ask a specialist in this area. 

If you do require LAMP, then that also can be setup manually, slightly more tricky but not rocket science. Main thing is to apt-get Apache first, then the rest, in that way the other components should more-or-less slot themselves in automatically when they see that Apache is present. If you do the reverse then you're left to manually edit the Apache extensions, which is daunting.

---

### Post by jtholt on 2007-11-04
I figured part of it out    what I needed to install was LTSP, however I only have one network interface and I would like to use LTSP along side my existing router. I cannot disable DHCP in my existing router.   Any Idias??

   also I am have a few different questions that have nothing to do with this   if you could help that would be great              

[http://ubuntuforums.org/showthread.php?p=3705831](http://ubuntuforums.org/showthread.php?p=3705831)

---

