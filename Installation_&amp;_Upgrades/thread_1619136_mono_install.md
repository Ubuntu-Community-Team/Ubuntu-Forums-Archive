---
title: "mono install"
date: 2010-11-11
forum: Installation &amp; Upgrades
---

### Post by leej23 on 2010-11-11
hi am trying to install mono-1.1.12.1. i have uninstalled other versions. i have the .bin file for mono but when i type ./mono-1.1.12.1_0-installer.bin nothing happens. i have made the it exacutuble but still nothing.

thanks lee

---

### Post by Cheesehead on 2010-11-11
Since the version of mono in the 10.10 Ubuntu repositories is currently 2.6.7, I do not understand why you are working to install an ancient version the hardest possible way.

Do you have your heart set on manually installing it? Are you aware of the other (easier) ways to get mono?

---

### Post by leej23 on 2010-11-11
> **Cheesehead said:**
> Since the version of mono in the 10.10 Ubuntu repositories is currently 2.6.7, I do not understand why you are working to install an ancient version the hardest possible way.

Do you have your heart set on manually installing it? Are you aware of the other (easier) ways to get mono?

i need this version for battlefield 2 admin tool for my server. newer versions dont work.
is there is an easyer way to install this.

---

### Post by Cheesehead on 2010-11-11
Well, that's a good reason all right.

Pardon me for a moment while I step out to eat my hat.
The oldest version in Ubuntu is 1.1.13.

Easier method: Look for a .deb with the version you want. There may be an archve out there somewhere with a version you can use. Use the 'gdebi' package to install the deb.

---

### Post by leej23 on 2010-11-11
> **Cheesehead said:**
> Well, that's a good reason all right.

Pardon me for a moment while I step out to eat my hat.
The oldest version in Ubuntu is 1.1.13.

Easier method: Look for a .deb with the version you want. There may be an archve out there somewhere with a version you can use. Use the 'gdebi' package to install the deb.


hi thnaks for you advice i have looked on the mono site for a ubuntu .deb an all there is are:

Ubuntu Dapper (6.06 LTS):  1.1.13.6

thats the earliest one but i need mono-1.1.12.1 anything after that isnt supported by the admin tool. 

i have been looking at ways to install the .bin seems simple enough i have followed the advice but nothing happens at all doesnt even try to install.

here is how i tried.

chmod +x mono-1.1.12.1_0-installer.bin

./mono-1.1.12.1_0-installer.bin

---

### Post by directhex on 2010-11-11
> **leej23 said:**
> i need this version for battlefield 2 admin tool for my server. newer versions dont work.
is there is an easyer way to install this.

Yes, newer versions DO work. They always have done.

But I'm bored of explaining how to people. You're not the first.

---

