---
title: "No Amarok in Ubuntu 7.10 i386?"
date: 2007-12-01
forum: Installation &amp; Upgrades
---

### Post by kaber on 2007-12-01
Hi,
Just installed Ubuntu 7.10 i386, it wont install or run Amarok or kaffine amongst other programs, say,s that Amarok cannot be installed on your computer type i386,and gave a couple of reasons,so what I would like to know is am I able to choose another instulation other than i386, here is what I have.
Celeron p4 1.7 m/b
500mg ram
160 gb h/drive
dvd combo burner.
adsl connection.
Kaber

---

### Post by monktbd on 2007-12-02
how did you try to install amarok or kaffeine? both need the kde libs which are not automatically installed with ubuntu. using synaptic and apt-get should resolve these depencies though.

---

### Post by forestpixie on 2007-12-02
are you sure your sources.list is ok, there are similar threads where things were commented out

Edit - if you're not sure, paste this into a terminal and post it here

```
cat /etc/apt/sources.list
```

---

### Post by dfreer on 2007-12-02
See above post.

Also, it would be helpful if you were to type:
```
sudo apt-get update
sudo apt-get install amarok
```
into the terminal, and post the results here.

---

### Post by kaber on 2007-12-02
Many thanks Guy,s
Fixed up the sourses.list and it worked fine, did not realize Ubuntu didn,t load the kde libs that was needed
kaber

---

### Post by forestpixie on 2007-12-02
can you mark thread solved

---

