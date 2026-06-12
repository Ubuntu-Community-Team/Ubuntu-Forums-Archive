---
title: "Root Password Problem"
date: 2005-04-11
forum: Installation &amp; Upgrades
---

### Post by evman on 2005-04-11
Don't know if this is common or not, but I was never supplied with a root password suring installation. I'm running the pre-release version of Hoary and I want to update it but I was never given a root password. Anyone know why? I tried installation twice and didn't get it.

Thanks

---

### Post by lukem on 2005-04-11
ubuntu does not have a root user in the sense that other OS's and even other distro's of linux do.  When ever you need to enter a command as root just start out with sudo.  Like 
sudo gedit filename
or whatever the command is that you need root to run.  

OH, you will be asked for a password but it is your own password.  The one you use whenever you boot up and log in.

If you try to run other programs from the desktop menu like Synaptic Package Manager or another program that asks for your password, it is the same.

Good luck and have fun

Luke

---

### Post by evman on 2005-04-11
Thanks a lot :razz:

---

### Post by Xgates on 2005-04-11
I really hate this sudo thing, it's bad security, someone gets into the user account then they have your box simpler than if there was a root password on it. Having that root password means twice the effort is needed to get root on the box, now with Ubuntu all they need to get is the user account to gain control. I hope Ubuntu might change this in the future.

---

### Post by Omega Blue on 2005-04-12
Also, sometimes I need to do a bunch of stuff as root. Not having a root account is a royal pain.  :-x

---

### Post by Perfect Storm on 2005-04-12
Then use root terminal. Applications ----> System tool ---> Root terminal.

---

### Post by danip on 2005-04-12
What about giving the option in the install to have the root account enabled or disabled?  Perhaps having disabled as default.

---

### Post by TedJ on 2005-04-12
If you need to enter several commands as root type 'sudo -s -H' and enter your password.

If the whole sudo setup annoys you, set a password for root with 'sudo passwd root' then remove yourself from the /etc/sudoers file.

BTW, as long as you pick a sensible password, the sudo setup isn't any less secure _from external attack_ than having root accessible. Heck, your personal login may be any name, but root is usually called root. ;)

---

### Post by ChrisTheGeek on 2005-04-12
I think the sudo approach is better overall since it's easier to understand for users 'you need to enter your password again' vs 'swap to root account' and means that less time is spent running with root privileges.  Arguably it also makes you think more beforehand since you have to type 'sudo' explicitly first making it obvious you are doing something potentially risky.

On a very nearly related note, does Ubuntu allow remote root sessions by default?  I know that SUSE disables this - can I do the same in Ubuntu?

---

