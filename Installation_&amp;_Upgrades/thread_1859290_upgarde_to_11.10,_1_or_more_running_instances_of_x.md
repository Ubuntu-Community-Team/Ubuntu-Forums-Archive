---
title: "upgarde to 11.10, 1 or more running instances of xscreensaver or xlockmore"
date: 2011-10-13
forum: Installation &amp; Upgrades
---

### Post by goodbye-windows(tm) on 2011-10-13
I just tried to upgrade Xubuntu to the new version (from 11.04 to 11.10). Everything went well until the very end of the process. 

I get the following error message:[U][B]




One or more running instances of xscreensaver or xlockmore have been detected on this system.  Because of incompatible library changes, the upgrade of the libpam-modules package will leave you unable to authenticate to these programs.  You should arrange for these programs to be restarted or stopped before continuing this upgrade, to avoid locking your users out of their current sessions.
[/B][/U]


It appears to me like my install is in limbo, because I don't know what the error message means and because I am warned NOT to proceed with the install.

I use only xubuntu, in a dedicated hard drive (no wubi). And, my system is a P4 at 3.2 GHz.

It sounds like I need to stop xscreensaver and xclockmore, then tell the install to proceed. Do I do this from the terminal mode, or do I terminate these by using the Task Manager.

I appreciate replies asap. as I can't use the computer until this problem is resolved.

TIA

Art

---

### Post by goodbye-windows(tm) on 2011-10-13
Here is additional info..........

I opened the Task Manager, and I have 'xscreensaver-nosplash' running. But, I see nothing named xlockmore running. 

So, I think I can use the Task Manager to temporarily stop 'xscreensaver', not sure what to do about the xlockmore issue.

Again, TIA.

Art

---

### Post by hmagoo on 2011-10-14
go into terminal application and type the next line and hit enter

killall xscreensaver

then type the next line and hit enter
killall xlockmore

I'm not sure if there is even a threat of you being locked out of your session like the warning says, but just to be sure I usually do that, listed above, whenever it gives me that warning.

on a side note.  I use xubuntu and 11.10 is really screwy for me so far.  Nautilus (not default app I know) is really messed up.

---

### Post by goodbye-windows(tm) on 2011-10-15
Hi HM,

Yes, I got it upgraded ok, thanks for your prompt reply. I was getting really concerned what would happen to my system if we had a brief brown out::>

I noticed there were tons of errors during the upgrade, most of which I didn't have a clue about. 

After the upgrade was completed however, I noticed the system ran much slower. If I could go back to 11.04, I'd do it immediately. I almost made a backup using clonezilla, just in case i wanted to go back....but I didn't do it. I'm not complaining-please don't misunderstand. It still runs faster than XP, and the fact that it is secure and otherwise viable is what's important to me. 

I have another system running XP and Xubuntu dual boot with wubi. The system is a Dell laptop with the dreaded black screen video problem. But, based on my experience with the latest 11.10, I think I'll just leave the laptop as is. 

I've completely transitioned over to Xubuntu, leaving windows behind. But,  there are 3 (small/minor) aps I need windows for, so I still maintain XP on the laptop. 

Regards,

Art

---

### Post by angelheart on 2012-04-26
@hmagoo

xubuntu 11.10 update to 12.04 had the same issue. CHEERS mate !!!

---

### Post by nl0s on 2013-04-28
@hmagoo and @angelheart

Xubuntu update from 12.10 to 13.04 also had the same issue. Thanks a lot for this info!

---

### Post by oldos2er on 2013-04-28
Old thread closed.

---

