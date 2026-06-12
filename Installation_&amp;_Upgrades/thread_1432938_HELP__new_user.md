---
title: "HELP * new user *"
date: 2010-03-18
forum: Installation &amp; Upgrades
---

### Post by BiiG on 2010-03-18
HEY opensource users :) 
am really new to linux .. i've installed ubuntu 9.10 through Wubi on windows vista home premium 32-bit laptop 
(Compaq presario cq60 , AMD athlon X2 250HDD , 4GB ram)
back to the problem,, i installed it 5 days ago, and i love IT and i was abt to  SWITCH grom windoWs !! but.. i downloaded a codec repository yesterday to play  movies and encrypted DVD-s from medibuntu .. then it told me to reboot , i did ,after the reboot there were updates i just clicked install and didnt see what it was cuz i was so sleepY
 and left it and went to sleep .. i woke up this morning ,, it told me to reboot again i did , then began the problem......

here's the pic ...

[http://www.zshare.net/image/73869383a1627790/]("http://www.zshare.net/image/73869383a1627790/")

and a pic with the possible commands ... * when i type in BOOT  it says : " error : no loaded kernel " 

[18032010009.jpg - 0.90MB](http://www.zshare.net/image/738706487f93b84c/)

plss guys heLp i love it SOOO MUUCH !! and srry abt the low LOW quality pics .... T.c

---

### Post by M!K3_$ on 2010-03-18
your getting a grub prompt?

---

### Post by M!K3_$ on 2010-03-18
your picture links are forbiden, so i can't look at them

---

### Post by lavinog on 2010-03-18
> **M!K3_$ said:**
> your picture links are forbiden, so i can't look at them

It is just a picture of the grub2 command prompt

---

### Post by M!K3_$ on 2010-03-18
ok, here's a solution

[http://ubuntuforums.org/showthread.php?t=1432367]("http://ubuntuforums.org/showthread.php?t=1432367")

by the way, consider creating better thread titles.
good luck.

---

### Post by lavinog on 2010-03-18
attached is a modified copy of the screenshot

---

### Post by BiiG on 2010-03-18
so you have any idea of what to do ? i understand it is  
" GNU GRUB version 1.97 beta4 " .....

---

### Post by M!K3_$ on 2010-03-18
> **BiiG said:**
> so you have any idea of what to do ? i understand it is  
" GNU GRUB version 1.97 beta4 " .....

look above

---

### Post by BiiG on 2010-03-18
am trying it now but .. what do i write as my kernel version ? is it 9.10 ?rlly srry for being a n00b guys ... and i will work on the title lolz XD

---

### Post by M!K3_$ on 2010-03-18
> **BiiG said:**
> am trying it now but .. what do i write as my kernel version ? is it 9.10 ?rlly srry for being a n00b guys ... and i will work on the title lolz XD

it's pretty easy because grub2 has tab completion. so start typing

linux /boot/vmli   (then hit tab)

it will stop, hit tab a few more times, it will show you all the possible kernel versions. find the latest kernel version and continue typing it then hit tab to finish it.

---

### Post by M!K3_$ on 2010-03-18
It tells you about all this in Omar's blog. It's not that long, read it.

---

### Post by BiiG on 2010-03-18
okay i did it that my kernel version is 2.6.31 .. but now it says  my windows partition ?? i hit tab it shows the possible files but, it doesn't write it for me .. should i just write " C: " ?? rlly rlly srry ....

---

### Post by M!K3_$ on 2010-03-18
Unfortunately, no.

Check Omar's Blog. You need to run

```
>ls -l
```

this will show you what hard drives/partitions you're using

> # hd(0,1) = /dev/sda1
# hd(0,2) = /dev/sda2
# hd(1,1) = /dev/sdb1
# hd(2,1) = /dev/sdc1

so if you have hd0,1 you will type in 

```

root=/dev/sda1
```

---

### Post by Arand on 2010-03-18
Answered similar question not long ago: [http://ubuntuforums.org/showthread.php?t=1430764](http://ubuntuforums.org/showthread.php?t=1430764)
And I would suggest an alternative (simpler, in my opinion) solution:
> **Arand said:**
> You might be seeing this issue: [https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/477104](https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/477104)

[https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/477104/comments/90](https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/477104/comments/90)
seems to be the primary workaround.
Probably a good idea to backup copy the current C:\wubildr before overwriting it.
- Arand

Booting Wubi manually through grub as described by others here is always a possible solution, though I'm guessing not the simplest.

EDIT: Ah seems like M!K3_$ already suggested this procedure first thing
I'll just agree then :) :ENDEDIT


- Arand

---

### Post by BiiG on 2010-03-18
my friend .. when i enter the second command "sh:grub> initrd /boot/initrd.img-2.6.31 " it still says u need to load the kernel first??

---

### Post by BiiG on 2010-03-18
u quit on me ? :P .. still not working !! pls i dont wanna use windowws ....

---

### Post by M!K3_$ on 2010-03-18
no, i went to work. but work is slow. so here i am again.

that just means you didn't complete the first part.

there are three parts to the "first part" ;)

show me what you're typing.

---

### Post by BiiG on 2010-03-18
i fixed it with  the " wubuilder "  ... it works :D:D  i rebooted twice to make sure ITS ALL GOOOD !! Thank You Guys Very Very Much ... and am srry again if i was a PAIN ! the thing is that nobody here even KNOWS abt linux and open source.. poor poor people lolz.. :)

---

### Post by M!K3_$ on 2010-03-18
> **BiiG said:**
> i fixed it with  the " wubuilder "  ... it works :D:D  i rebooted twice to make sure ITS ALL GOOOD !! Thank You Guys Very Very Much ... and am srry again if i was a PAIN ! the thing is that nobody here even KNOWS abt linux and open source.. poor poor people lolz.. :)

You downloaded the file and replaced it, or you used an application?

No pain at all, keeps me busy. :D

Also, most people on this forum come here for help. Like yourself for instance; I saw that this is your first thread. 

I first came here not knowing a thing about linux to, plus my spelling was really bad back then. ;)

---

### Post by M!K3_$ on 2010-03-18
lol,
[http://ubuntuforums.org/showthread.php?t=137431]("http://ubuntuforums.org/showthread.php?t=137431")

That was my first thread.

---

### Post by BiiG on 2010-03-18
i just replaced it..:) but i understand it's temporary ? how ?

lolz @ first thread you were so straight forward !!

hey man do you recommend me to switch from windows ?

---

### Post by M!K3_$ on 2010-03-18
> **BiiG said:**
> i just replaced it..:) but i understand it's temporary ? how ?

lolz @ first thread you were so straight forward !!

hey man do you recommend me to switch from windows ?

I lost the launchpad page where I got the info from, and thus I forget why its a temporary fix. Anybody else like to fill us in?

My first thread was so brutal. lol

If you feel comfortable enough and Linux provides you will all the applications you need, go for it. Windows still gives me a few features that linux can't provide, so I use both.

---

### Post by BiiG on 2010-03-18
alright man.:) 

btw.. any advice on linux in general ? thnx allot man your awesOME!! :D

---

### Post by M!K3_$ on 2010-03-18
change this thread to solved. as far as linux. just play with it. try to solve the problems you have. hang out on here. try to help other people

---

### Post by BiiG on 2010-03-18
oki man .. cya later and thanks again

---

