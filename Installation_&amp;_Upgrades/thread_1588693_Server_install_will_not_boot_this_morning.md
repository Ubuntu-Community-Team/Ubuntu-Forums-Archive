---
title: "Server install will not boot this morning"
date: 2010-10-05
forum: Installation &amp; Upgrades
---

### Post by hasafraker on 2010-10-05
first, this box is running 10.04 server, it's been running perfectly for almost 6 weeks. It's only function in life is running MailArchiva which is an ediscovery package, runs very well. Anyhow, yesterday the boss tells me he wants to do something else so the last thing I did was an apt-get update and an apt-get upgrade, no errors were observed, I seem to remember like 8 updates were available, this is what I've normally done in the past to keep it current. The last thing I did after that was shutdown -r now. This morning I can't get into the box, I reconnected a monitor to it and this is the error I'm getting when it stops after about 9 lines into the boot process;

modprobe: FATAL: Error inserting padlock_sha (/lib/modules/2.6.32-24-server/kernel/drivers/crypto/padlock-sha.ko): No such device. 

This is a mystery to me, the system is not encrypted. The only stuff that is belongs to MailArchiva. Anyhow someone evidently made off with my install cd so I am downloading another to see if I can repair this but I have no idea what broke. Any ideas?

thanks

---

### Post by ronparent on 2010-10-05
Just a thought. Boot to the recovery mode and run dpkg in the recovery menu. It may not fix the problem but it will show any update problem and which modules are involved.

---

### Post by hasafraker on 2010-10-05
not having a lot of luck with recovery mode but thanks for the idea. I can't seem to make any progress with it. I'm sure if I'd just blow the system away, reinstalled the server and started importing all the data I'd be nearly done by now. It's a shame, nothing I did yesterday should have blown the system up like this.

---

### Post by hasafraker on 2010-10-05
ok well miracles never cease, I've been beating on this thing all day, and trying different searches to see if I'm just not searching on the right thing. By some miracle I caught this little link under several other results almost like a sub-set of search results but this thread details almost exactly the error message I was getting  [http://ubuntuforums.org/showthread.php?t=1521336](http://ubuntuforums.org/showthread.php?t=1521336)  I booted to my server disk, launched a recovery console, opened up /etc/fstab in vi and commented out the one line for this samba share that I'd setup originally to import the email data from an archive and then tried to boot the server again, I was distracted by the phone for a moment and when I looked back it was actually at a login prompt! It would seem that a few other settings have been reset to defaults like my static ip setup but that's easy enough to fix.

Hope this maybe helps someone else too.

I'm not sure why this samba share I setup would be causing me grief but certainly commenting out the line in fstab that was calling it fixed the problem. I've reset a couple things and the box is now working as it was before.

---

### Post by ronparent on 2010-10-05
Glad to hear you worked your way out of it. Good luck.

---

