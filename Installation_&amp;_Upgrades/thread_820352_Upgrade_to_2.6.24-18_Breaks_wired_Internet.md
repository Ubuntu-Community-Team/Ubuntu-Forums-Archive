---
title: "Upgrade to 2.6.24-18 Breaks wired Internet"
date: 2008-06-06
forum: Installation &amp; Upgrades
---

### Post by Ed1P on 2008-06-06
Luckily I'm running Ubuntu on a VMWare Guest account, so I keep a full system backup. As you will find out, upgrading to 2.6.24-18 will cause a minor disaster and totally break your internet connection on rebooting.

This is a reported bug, and it seems the cause is that the upgrade package didn't install linux-ubuntu-modules-2.6.24-18-generic as a dependency.

I'm one of those people who falls between the nube and competent Linux user, so I haven't got a clue how to fix this problem. Can anyone help?

I now have two broken versions, one which has unfortunately been rebooted, and one in an un-rebooted state, so I can easily test possible solutions.

Thanks in advance - Ed

---

### Post by gladgrad on 2008-06-06
I also have a similar problem - I think it first happened with 2.6.24-17.  When I saw 2.6.24-18 avaiable so quickly afterwards I assumed that was the fix - but it appears not.

I have found that I can get to a working system by booting into the kernel recovery mode and going through the recovery options there - but I don't want to do that every time I turn the machine on.

---

### Post by Ed1P on 2008-06-06
This cured most of the problem: [http://ubuntuforums.org/showthread.php?t=818241](http://ubuntuforums.org/showthread.php?t=818241). Unfortunately, my wired connection now fails to autostart - you need to watch out for it as it will appear that the 'cure' does not work. Just make sure you have a 'Network Monitor' in your panel to turn it on.

Anyone know how to fix the 'network auto-start' problem?

Incidentally, be VERY careful applying the 'delete old generics'. This is a fundementally unsafe procedure. Anyone know a better way of rebuilding the module more safely?

---

