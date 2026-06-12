---
title: "I thought they were gonna have the Dual Boot issues resolved with Alpha 3"
date: 2009-07-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by theozzlives on 2009-07-23
Or have they and mines not setup correctly? I don't know enough about GRUB2 to check. My Win XP "Fax Machine" is on SDA and Karmic is on SDB. I want to try Karmic on something other than a VirtualBox. Is Legacy GRUB still an option, and can I install it on an existing system?

---

### Post by agel1 on 2009-07-23
they didn't include firefox 3.5 either.!

---

### Post by wayne_cat on 2009-07-23
grub is still available ... I'm using it

```
root@macbook:~# apt-cache policy grub
grub:
  Installed: 0.97-29ubuntu56
  Candidate: 0.97-29ubuntu56
  Version table:
 *** 0.97-29ubuntu56 0
        500 http://archive.ubuntu.com karmic/main Packages
        100 /var/lib/dpkg/status
root@macbook:~# 
 
```

---

### Post by ranch hand on 2009-07-24
You should not have any trouble with Grub2 on a setup like that.

Install 9.10-A3.  Reeboot into 9.10.  If XP is not on the menu, lucky you (I didn't mean to say that), fire up the terminal and;
```

sudo update-grub

```
and try booting again.  I bet it works.

If not;
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

I have had a great time with grub2 for about the last 10 to 14 days.  I even have hade it shitched from the last install to the 3rd of 7 OS' installed with / on sda and /home on sdb.  There was a time that it would not boot from there at all unless run through grub .97.

---

### Post by theozzlives on 2009-07-24
> **ranch hand said:**
> You should not have any trouble with Grub2 on a setup like that.

Install 9.10-A3.  Reeboot into 9.10.  If XP is not on the menu, lucky you (I didn't mean to say that), fire up the terminal and;
```

sudo update-grub

```
and try booting again.  I bet it works.

If not;
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

I have had a great time with grub2 for about the last 10 to 14 days.  I even have hade it shitched from the last install to the 3rd of 7 OS' installed with / on sda and /home on sdb.  There was a time that it would not boot from there at all unless run through grub .97.

I did that last night and got GRUB legacy. I know Windows is a P.O.S. but so is the computer. their made for each other, haha. I need it til I figure out how to send and recieve faxes with a winmodem in Ubuntu.

---

### Post by flavouride on 2009-07-24
please umount the xp partition first before "sudo update-grub"

---

### Post by theozzlives on 2009-07-25
> **ranch hand said:**
> You should not have any trouble with Grub2 on a setup like that.

Install 9.10-A3.  Reeboot into 9.10.  If XP is not on the menu, lucky you (I didn't mean to say that), fire up the terminal and;
```

sudo update-grub

```
and try booting again.  I bet it works.

If not;
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

I have had a great time with grub2 for about the last 10 to 14 days.  I even have hade it shitched from the last install to the 3rd of 7 OS' installed with / on sda and /home on sdb.  There was a time that it would not boot from there at all unless run through grub .97.

update-grub did it thanks

---

### Post by ranch hand on 2009-07-25
I am happy.  That is the way it should work.

Grub-legacy is something that I have come to really love.  I think that the new grub may be even better.

---

