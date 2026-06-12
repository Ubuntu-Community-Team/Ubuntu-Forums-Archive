---
title: "Dual boot issue"
date: 2007-05-16
forum: Installation &amp; Upgrades
---

### Post by twistedtwig on 2007-05-16
Hi all,

I recently decided to set up my first dual boot as I want to migrate across to linux but cant give up windows just yet :p

I partitioned my hard drive (2 hard drives installed, one for OS's and one for Data).  its a 80 GB drive for the OS which was split 50 / 50... I installed XP Pro onto the second partition and got that all udpated etc.

I then tried to instal 7.04 onto the first partition.  The first time the grub didnt install correctly.  The next morning I re ran the install and it all went in fine.

It will now boot into linux but I get no option to boot into windows.  I presume the boot.ini or something simlar has gone wrong.  I intend to try and run the windows CD and do the repair feature to hopefully try and fix this tonight (when I get home from work).. I was hoping someone might have any thoughts suggestions before then if this is not the right path to follow or any better suggestions.

In windows the C drive was the empty one ready for Ubuntu, F drive was data drive and I was the windows OS.  I don't know much about the boot strapping process and if windows would have been stupid enough to put its boot bits on the C drive and it got blatted (technical term :p) when I installed Ubuntu.

Any and all thoughts / suggestions would be gratefully received.

Thanks

---

### Post by Tautoa on 2007-05-17
As far as I know, the repair feature on the Windows CD will mess with (another technical term) the Master Boot Record, when you restart, you would boot straight into Windows, without the option of booting into Ubuntu. 
I would try re-installing GRUB, in the hope that it would detect both OSs.
Also, from what I've read, Windows is very self-important, if it's not on the first partition of the master hard-drive, it might cause problems for you. Can anyone confirm this? Everything I've said here is just what I picked up while looking for a solution to a different problem.

---

### Post by twistedtwig on 2007-05-21
Hi I figured it out... you are right that windows is a silly thing.  It doesn't like being anywhere apart form on the first partition, (at least that solved it for me).  Got them both in and running (just a million updates to do now)!

Thanks

---

