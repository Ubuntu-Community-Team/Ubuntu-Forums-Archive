---
title: "Postgre 8.3 on Ubuntu 10.04 LTS"
date: 2011-04-19
forum: Installation &amp; Upgrades
---

### Post by irfans on 2011-04-19
The default postgresql available on 10.04 is 8.4 but I need to have 8.3. 
How do I install it?

---

### Post by Dutch70 on 2011-04-19
You should be able to download it and get the installation instructions from here...
[[COLOR="RoyalBlue"]Download[/COLOR]]("http://www.postgresql.org/")
[[COLOR="RoyalBlue"]Documentation[/COLOR]]("http://www.postgresql.org/docs/")

---

### Post by irfans on 2011-04-19
Thanks Dutch but the postgresql official documentation does not really help.
Is there any way I can get the Postgresql 8.3 in the 10.04 repository?

---

### Post by Dutch70 on 2011-04-20
Not that I know of, but that's not really saying much. :P

I believe if you can find a DEB package, it will be very easy to install with software center. There are some in the following link, but they don't seem to go back to 8.3.
[[COLOR="RoyalBlue"]http://www.openscg.org/se/postgresql/archive-packages.jsp[/COLOR]]("http://www.openscg.org/se/postgresql/archive-packages.jsp")

---

### Post by irfans on 2011-04-20
I could get the bin file(postgresql-8.3.15-1-linux-x64.bin) for postgre 8.3.
To install I ran the followong commands,
 chmod a+x binfile
 sudo ./binfile

 This gives an error,
 ./postgresql-8.3.15-1-linux-x64.bin: 3: Syntax error: ")" unexpected

 Whats possibly going wrong ?

---

### Post by irfans on 2011-04-20
I was finally able to install postgresql 8.3 following the below steps,

You should be able to use any of the listed mirrors by adding a line to your /etc/apt/sources.list like this:
  deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main 

Then using the Synaptic manager apply the packages for 8.3..
Finally run apt-get install postgresql-8.3 :D

---

### Post by Dutch70 on 2011-04-20
Nice! Thanks for posting your solution irfans. :)

People will be more likely to find & use it if you mark it [Solved] with "Thread Tools" at the top of the page.

---

