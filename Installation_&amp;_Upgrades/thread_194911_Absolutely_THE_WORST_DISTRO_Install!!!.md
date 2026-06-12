---
title: "Absolutely THE WORST DISTRO Install!!!"
date: 2006-06-12
forum: Installation &amp; Upgrades
---

### Post by mpierce on 2006-06-12
I love ubuntu and what you're doing but here's my two cents!!!

Kubuntu should be ashamed of themselves for releasing Dapper. 
I've downloaded the iso from two sources. BOTH desktop distro installs froze and refused to install. 

I then downloaded the alternate 6.06 iso and what do I get, corrupt files, iproute and initramfs-tools; this prevented the system from bootstraping. Another waste of time and bandwidth.  

A whole day wasted and I've been using Linux since early RedHat 5.x days. Now this doesn't make me the smartest end-user just one who can generally install a distro without problem. 

The new install is cute and would have been a joy for any Window user comtemplating a switch to Kubuntu. What they will encounter is a reason to leave Linux and say, I told you so. 

If I can't get a system installed, I know they can't. Think I'll go back to 5.10 it worked perfectly.

Shame on you!!! And, I really mean it. What a waste of time. The forum is full of problem after problem trying to install it. 

It needs to be fixed and the fixed publicly announced.

---

### Post by HighPlainsDrifter on 2006-06-12
In my experience, which is a lot of experience, corrupted install files usually indicate a bad burn/physical problem with your CD or the CD burner itself, or the ISO was not downloaded correctly... In this situation, md5sums are your friend.

---

### Post by fireshell on 2006-06-12
Ive had no problems with it, and many other people are happy to use it. Maybe you need to stick with 5.10 if your having difficulties with it?

---

### Post by xfile087 on 2006-06-12
[QUOTE=HighPlainsDrifter]In my experience, which is a lot of experience, corrupted install files usually indicate a bad burn/physical problem with your CD or the CD burner itself, or the ISO was not downloaded correctly... In this situation, md5sums are your friend.[/QUOTE]

I second that. When I first downloaded and installed Ubuntu Dapper Drake DVD - the installer came up with errors multiple times. I went to another machine, burnt a CD version instead. It works perfect and i'm currently running Dapper Drake!

---

### Post by fmo on 2006-06-12
> **mpierce]I love ubuntu and what you're doing but here's my two cents!!!

Kubuntu should be ashamed of themselves for releasing Dapper. 
I've downloaded the iso from two sources. BOTH desktop distro installs froze and refused to install. [/quote]

Are you sure of your Sources? did you MD5SUM the ISO image?

[QUOTE=mpierce]I then downloaded the alternate 6.06 iso and what do I get, corrupt files, iproute and initramfs-tools said:**
> 

Same suggestion as before, what you can also try is just installing a base minimal system and do from command line "sudo apt-get install kubuntu-desktop"

[QUOTE=mpierce]The new install is cute and would have been a joy for any Window user comtemplating a switch to Kubuntu. What they will encounter is a reason to leave Linux and say, I told you so. 

Obviously the problem is not with the graphic installer since you have problems with the text installer too.

[QUOTE=mpierce]If I can't get a system installed, I know they can't. Think I'll go back to 5.10 it worked perfectly.

Shame on you!!! And, I really mean it. What a waste of time. The forum is full of problem after problem trying to install it. 

It needs to be fixed and the fixed publicly announced.[/QUOTE]

If the Breezy installer works fine for you, what about doing a clean install of Breezy and then a "dist-upgrade" to Dapper?

Seriously, I understand your frustration, and I really think that it's what is talking now, I hope that you can solve you problem because Dapper is really a great distro !

And remember about those comments on the forum, you always hear more about people having problems than people who haven't, I have a friend that doesn't understand anything about computers and installed a fully functionnal Dapper system in 1hour and a half (thanks to Automatix), so it can't be that bad ;-) 

Good luck with your install

---

### Post by mpierce on 2006-06-12
Thanks for all the wonderful advice. I knew how to use md5sum and have used it. Thought I'd give Dapper another try. So, downloaded from another source. Did md5sum *.iso (it has a name that I used). Bit redundant doing this since k3b does this prior to burning. md5sums match. 

Insert new cd - oh no, bootstrap failure again!

Warning: file:///cdrom/pool/main/j/jfsutils/jfsutils_1.1.8-1_i386.deb was corrupt

---

### Post by frenkel on 2006-06-12
[QUOTE=mpierce]Thanks for all the wonderful advice. I knew how to use md5sum and have used it. Thought I'd give Dapper another try. So, downloaded from another source. Did md5sum *.iso (it has a name that I used). Bit redundant doing this since k3b does this prior to burning. md5sums match. 

Insert new cd - oh no, bootstrap failure again!

Warning: file:///cdrom/pool/main/j/jfsutils/jfsutils_1.1.8-1_i386.deb was corrupt[/QUOTE]
Are you sure your CD drive is not broken? Is the lens clean? (no dust on it?)

---

### Post by vinodis on 2006-06-12
Go get windows. its very easy to click on and pay.

---

### Post by Gustav on 2006-06-12
Sometimes it helps to burn the CD at very slow speed (4x).

---

### Post by devurandom on 2006-06-12
You have a corrupted CD / your drive is not working correctly.
I had this issue. I burned 2 kubuntu ISO on 2 cd-r of low quality and they froze when trying to mount root filesystem.

I burned a dvd and it worked flawlessly.

I noticed that the same cd, read by inside an OS, can look good, but because the OS (be it windows or linux) does attemps to read until it can. Booting live cds seem to do less attempts (or none) to read it correctly, so they're far more sensitive to imperfections. I noticed it not only on kubuntu but on dozens of live cds -they look perfect when mastered, but they won't boot because they are not perfect.

[B]
Shame on you!!! And, I really mean it. What a waste of time. The forum is full of problem after problem trying to install it. [/B]

Shame on you for accusing developers etc. of problems that are CLEARLY not related to the actual release of Kubuntu. No sane developer team would release something with corrupted files unable to boot, I hope you're smart enough to understand it.

---

### Post by megamania on 2006-06-12
[QUOTE=mpierce]Thanks for all the wonderful advice. I knew how to use md5sum and have used it. Thought I'd give Dapper another try. [/QUOTE]

If ISO = ok AND CD = not_ok
then
 CD = faulty
 blame = ubuntu
 flame = true
 brain = off
endif


(sorry about that)

---

### Post by vinboy on 2006-06-13
I downloaded the Kubuntu Dapper Release Candidate and it worked. Installed perferctly.
Except that it formatted my whole harddisk when I told it to resize my partition.

My best guess is you have a corrupted download.

and don't shout at the developers as they are doing this for free, if you are as good as you said you are, you should go start your own distribution and stop complaining.

[-X

---

### Post by SkyNet2029 on 2006-06-24
As stated ad nauseum, burn it at a lower speed or do a substitution on your install media, (don't use the el-cheapo's). And just because the machine that 
burned your media can read it does not mean every machine will be able to.
At any rate, just wanted to add that it is in extremely poor taste to rant and be a troll just because your vast linux elitism.. I mean experience...would not get you past a little installatioin woes. There are many different setup routines you can toss at your kernel when booting , but you probably already knew that.
Enjoy Windows, as you are clearly one of those confused little sheep that thinks everything should be plug and pray..ermm. play.
](*,)

---

### Post by blackbeastofaarrgh on 2006-06-26
I say replace your CD burner. I had this problem awhile back. But I, being the wonderful (and slightly arrogant) person I am, didn't blame the developers and instead figured out that my CD drive was dead.
You can find a good CD-RW/DVD-R for about $40 at Wal-Mart if you live in the USA.
Remember kids, trolling is bad!

---

