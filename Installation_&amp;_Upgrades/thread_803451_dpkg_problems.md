---
title: "dpkg problems"
date: 2008-05-22
forum: Installation &amp; Upgrades
---

### Post by Mathiasdm on 2008-05-22
During an update (after installing Hardy 8.04), my computer crashed (I had an APIC error), which seems to have corrupted dpkg.

When I go to System > Management > Update-Manager, I get a warning telling me to run
[PHP]dpkg --configure -a[/PHP]
because dpkg was interrupted.

When I run that command, I get the following output:
[PHP]dpkg: parse error, in file `/var/lib/dpkg/updates/0052' near line 1:
 nieuwe regel in veldnaam `padding'
[/PHP]

I then tried [PHP]sudo dpkg --clear-avail[/PHP], that seemed to work (no output).

Next, I ran [PHP]sudo apt-get update[/PHP] and got (after a list of repositories):
[PHP]E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. [/PHP]

So I'm kind of in an infinite loop here :( Suggestions are welcome.

---

### Post by Mathiasdm on 2008-05-22
Wow, problem solved :)
I simply deleted [PHP]/var/lib/dpkg/updates/0052[/PHP]

---

### Post by Bmanery on 2008-05-22
> **Mathiasdm said:**
> Wow, problem solved :)
I simply deleted [PHP]/var/lib/dpkg/updates/0052[/PHP]
I'm a real newbe!
could you please tell me how and where you placed the PHP Code.
I'm having the same problem and need to use the code.

---

### Post by decoherence on 2008-05-22
It's not actually PHP Code, it's just marked as such.

To do these things, go to Applications>Accessories>Terminal

Assuming you're having this problem, my suggestion would be to try the following commands, one after the other

```

sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
sudo apt-get dist-upgrade
```

Just so you are aware, prefacing the commands with 'sudo' will ask for your password, just like the Update Manager does when you install packages. In the terminal your password is not echoed back to you, even as little dots. Just type it and press Enter. 

That should get you cleaned up and back on the right track. Personally, I've never had to delete one of these update files, and I'd rather not tell you to 'sudo rm' anything as even an innocent typo can cause damage with the rm (remove/delete) command.

---

