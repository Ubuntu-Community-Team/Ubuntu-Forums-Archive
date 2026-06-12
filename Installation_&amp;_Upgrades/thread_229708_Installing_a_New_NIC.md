---
title: "Installing a New NIC"
date: 2006-08-04
forum: Installation &amp; Upgrades
---

### Post by MasterXandrex on 2006-08-04
Hi All,

I have been using linux for a while now... first redhat, then ubuntu (Hoary), then Gentoo, and now I'm back to Ubuntu.

In all that time, I've never done much with hardware... all software and development, web administration and the like. I've come across a problem and I don't know how to fix it...

My NIC died on me and I've never swapped hardware on a linux box after the install and I have to admit: I don't know where to start.

Please Help Me,

Thanks

UU

Forgot to put down the symptoms... If the NIC is in alone, there is no listing on ifconfig. If it's with the bad NIC, only the bad NIC has a listing. It is listed in lspci.

---

### Post by cantormath on 2006-08-04
> **UbuntuUser3859 said:**
> Hi All,

I have been using linux for a while now... first redhat, then ubuntu (Hoary), then Gentoo, and now I'm back to Ubuntu.

In all that time, I've never done much with hardware... all software and development, web administration and the like. I've come across a problem and I don't know how to fix it...

My NIC died on me and I've never swapped hardware on a linux box after the install and I have to admit: I don't know where to start.

Please Help Me,

Thanks

UU

What kinda hardware do you have?  Desktop, laptop....Wireless? MAC?
I would think that you have a PCI NIC.  If you dont know, take the old nic out, and take it to the store.  Show them what you have and that you need a new one.  Buy a new one.  Most all of them will work, assuming you have a none mac PC.  Should be [10-20]("http://www.newegg.com/ProductSort/SubCategory.asp?SubCategory=27") dollars.  Just dont buy a brand that is some wierd company no one has heard of.  

Take the new one how and put it back in.  Boot up, and it _should_ be there. and connect to the internet the same way.

If you are looking for a play by play tutorial, I will look for one.

---

### Post by MasterXandrex on 2006-08-04
As a matter of fact, I did exactly that... I went to the store looking for my current NIC (Linksys LNE100TX-G1 PCI) however, the only one they had was a Linksys LNE100TX-G5 PCI. My current (or rather my old) NIC is no longer manufactured. I thought that these two being very similar would allow me to swap them, it does not...

Not only that, I would actually like to know how to swap out hardware in a live installation.

Thanks

---

### Post by cantormath on 2006-08-04
> **UbuntuUser3859 said:**
> 
Not only that, I would actually like to know how to swap out hardware in a live installation.

Thanks


Live installation?

Im really suprised about the new card not picking up.  What kind of hardware do you have, how old?....

---

### Post by MasterXandrex on 2006-08-04
Well, it is a few years old, not my main box just one I use as an Apache and Proxy server. It's a Pentium III 1.1 GHz with 512 MB ram and two 60Gb hard drives. I know you were probably looking for more specifics on my mother board, but I really can't give them to you... it's a Gateway that I inherited and I don't know much more about it than that. 

By live installation I mean to install a new NIC (or other hardware) without reformatting and reinstalling.

Thanks,

UU

---

### Post by MasterXandrex on 2006-08-04
Just an update, figured it out

looked into /etc/network/interfaces

no listing for eth1... created one and poof

... well, atleast for a little while, until I rebooted and now it won't come up... i've removed the entry

---

### Post by cantormath on 2006-08-04
> **UbuntuUser3859 said:**
> Just an update, figured it out

looked into /etc/network/interfaces

no listing for eth1... created one and poof.

good talk

---

### Post by MasterXandrex on 2006-08-04
like I was saying... worked for a bit... then nothing

---

