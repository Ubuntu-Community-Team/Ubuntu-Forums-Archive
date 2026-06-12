---
title: "Upgrade ubuntu 11.10 freeze in the logo with msg below no network configuration"
date: 2011-10-17
forum: Installation &amp; Upgrades
---

### Post by jao_madn on 2011-10-17
Hi,

I just upgrade my 11.04 to 11.10 last 2 days ang after i upgrade my system wont boot ang stay freezes forever in the logo with a msgs below state that the system will boot without network configuration. by the way before that happen the system show msgs about configure the network and again wait for 60 seconds to configure..

Is somebody also suffer this problem..if there are can u tell us what did u do to solve the issue..

Thanks for any responce..

---

### Post by 23dornot23d on 2011-10-17
Check my link below for failed upgrades you may find a solution in there ....

similar things have already been solved ....

---

### Post by jao_madn on 2011-10-18
Hi all,

Finally i finish and sort out all of my problems in 11.10 for the meantime...

My problem are pretty discribe on this blog here
[Upgrade to Ubuntu 11.10 problem: Waiting for network configuration then black screen solution]("http://uksysadmin.wordpress.com/2011/10/14/upgrade-to-ubuntu-11-10-problem-waiting-for-network-configuration-then-black-screen-solution/")
This is exactly perfect on my problem but for i never try the solution since i found this blog after i fresh install the 11.10 from livecd.

Althoug i encounter a problem even in the fresh install and the problem i cannot login in my user account but in guess account it works fine, i can use my login user and password in login tty terminal using crtl+alt+Fn(1,2,3...) but not in gui..After looking arount for the solution i foung this blog [Ubuntu 11.10 cannot login and cannot shut down]("http://www.linuxquestions.org/questions/ubuntu-63/ubuntu-11-10-cannot-login-and-cannot-shut-down-907558/") and it works for me..The solution is login in terminal using ctrl+alt+fn and change the user and group of the home directory using this command sudo chown -R user:user..

It seems odd as i first check my home is in 500:500, root and other permission.
In my own analysis i think the cause of the problem in my fresh installation is i didn't assign to reformat the home partition before installing files since i rename my old home dir just in case some files needed so i never reformat and just point during the installation where the home partition must mount. Im not sure thought..

---

