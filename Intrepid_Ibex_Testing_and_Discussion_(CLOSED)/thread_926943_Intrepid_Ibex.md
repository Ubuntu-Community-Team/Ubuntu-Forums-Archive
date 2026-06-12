---
title: "Intrepid Ibex"
date: 2008-09-22
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Andrew79 on 2008-09-22
Just curious folks, when the new version comes out, all your stuff, will it transfer? Like photos, music, video. Or will it be a clean install? What if I use the terminal to upgrade?

---

### Post by clive littlewood on 2008-09-22
Hi

You will be notified of the new version in updates.If you just update then all your photos, files ect. will still be there.

Many people choose to do a clean install, but you would then have to backup your files to usb stick or equivelent and then transfer back.

Hope this helps

cl

---

### Post by Dougie187 on 2008-09-22
If you use the terminal to upgrade, or the upgrade manager, it will just be like installing a new kernel. So everything will transfer, if you want to think of it that way.

If you download the cd, and do a fresh install, and you *DON'T* have a seperate home partition, then none of your stuff with transfer unless you do it manually. From my experiences, you typically get a better experience if you do a fresh install then if you upgrade, but some people like upgrading more. So in the end its up to you how you want to do it.

---

### Post by waspbr on 2008-09-22
provided you wanna try it, you can just upgrade, although it is always advisable to back up your files just in case something may go wrong(unlikely but possible).

To try out other distros it is hand to have either a /home partition  or to have installations on different partitions. 

I have to stress that upgrading at this stage is very risky, it's better to wait until the stable release comes out.

---

### Post by Tatty on 2008-09-22
Before any OS install or upgrade you should always back up all your personal data, as things can sometimes go wrong.

The easiest thing for you then would be to do a dist upgrade.  Update manager should alert you to a new distro and give you an option of upgrading, which should preserve your /home.

Alternatively, if you have a separate partition for /home then its pretty easy to just install over your current / partition and use your old /home.

I recall reading that there were plans to allow /home to be preserved in a standard install since hardy, but i dont know if this is has happened.

---

### Post by Het Irv on 2008-09-22
Last time around I did a compleat reinstall and it took me a while to get it back to where I wanted it.  I think this time I am going to do a backup and then just update though the terminal ( I plan on switching when Beta is out).

---

### Post by Mornedhel on 2008-09-22
What's the status on a full upgrade currently ?

I tried that on Dapper > Edgy and Edgy > Feisty, and it broke both times.

Had to do clean reinstalls for Edgy and Feisty in the end, and since then I never even tried for Gutsy and Hardy. I heard it worked better but never tried.

---

### Post by Tatty on 2008-09-22
> **Mornedhel said:**
> What's the status on a full upgrade currently ?

I tried that on Dapper > Edgy and Edgy > Feisty, and it broke both times.

Had to do clean reinstalls for Edgy and Feisty in the end, and since then I never even tried for Gutsy and Hardy. I heard it worked better but never tried.

Well, as with everything computery, it should work, but sometimes doesnt.

I have sucessfully upgraded dapper->edgy and feisty->gutsy, but now i prefer to do clean installs as it just leaves everything tidier.

---

### Post by waspbr on 2008-09-22
I just did the intrepid upgrade on my desktop and it did not go so well, can't boot from it, but I have a /home partition and I have other distros(linuxmint and pclos) installed in other partitions so not worries there.

@ Het Irv - you might want to consider making a /home partition, it makes life a whole lot easier

---

### Post by Het Irv on 2008-09-22
> **waspbr said:**
> I just did the intrepid upgrade on my desktop and it did not go so well, can't boot from it, but I have a /home partition and I have other distros(linuxmint and pclos) installed in other partitions so not worries there.

@ Het Irv - you might want to consider making a /home partition, it makes life a whole lot easier
No kidding, thats something I havn't gotten around to doing yet, but I really should.  Especially since I have been trying some other distros.

---

### Post by hyper_ch on 2008-09-22
> **Tatty said:**
> Before any OS install or upgrade you should always back up all your personal data, as things can sometimes go wrong.

I partially disagree here... not only when you are going to do something "serious" on your computer you should make backups... but you should make backups regurarly.

---

### Post by rain4ever on 2008-09-22
> **waspbr said:**
> I just did the intrepid upgrade on my desktop and it did not go so well, can't boot from it, but I have a /home partition and I have other distros(linuxmint and pclos) installed in other partitions so not worries there.

@ Het Irv - you might want to consider making a /home partition, it makes life a whole lot easier

I also installed the intrepid upgrade and i couldn't boot from it at first. but I then pulled out the boot menu and told it to run from last successful boot. I then updated My computer again, and all went fine when booting up again. This is just my personal experience with it. The reason I did the install in the first place was because of the kernel that made working with atheros a lot easier. It's still in alpha stages so update at your own risk.

---

### Post by rosswmcgee on 2008-09-22
I run two Ubuntu computers. One has been upgraded all the way through since dapper, with no problems. The other upgraded only from Edgy. The older one is running slower, so I will do a clean install after Intrepid Ibex, is released.

---

