---
title: "Backup"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by ART_Adventures on 2007-04-20
Hello People,

I want to upgrade to Feisty, but the upgrade doesn't work for me. So I was planning to do a clean install. Before I do this, however, I want to backup my emails in evolution so that after re-installing I can import them back. How can I do this?

Thanks.

---

### Post by kidders on 2007-04-21
Hi there,

In theory, everything you need to move a user from one Linux installation to another should be in his home directory. Applications are not supposed to write anything user-specific to any other location.

If I needed to back up a user's data, I would make a tarball of his ~ and put it to one side.

```
sudo tar czf home.tar.gz /home/username
```Three additional suggestions:[LIST]
[*]To make life easier for myself, I would then do something like **grep `whoami` /etc/passwd | cut -d: -f3**, note down the number (which should be something around 1000), and be sure to recreate the user on the new install using the same UID. That way, you won't have to go fiddling with permissions ... which is especially handy if you're like me and have stuff (eg movies, mp3s...) that belongs to that account scattered over multiple hard disks.
[*]Before doing anything irreversible, you should check the documentation for any applications (eg Evolution) whose preferences you want to preserve, just to be _sure_ they don't break the rules, and store critical user data in a non-standard location.
[*]You might also like to think about copying some other locations. For instance...[LIST]
[*]MySQL databases ordinarily live at /var/lib/mysql.
[*]System-wide websites are usually kept in /var/www.
[*]The installer archives for applications you've installed should be at /var/cache/apt/archives. For convenience, you might want to rescue anything you *can't* get out of Ubuntu's standard repositories, so you don't have to go looking for them again.
[*]System-wide application configuration lives in /etc. Over time, people often accumulate settings that may have been difficult to figure out, non-standard, or time-consuming to recreate. For instance, you might feel particularly attached to your Samba config, or your current repository list. Having a tarball of /etc to hand for reference can make setting up your new system easier, if you tend to like things a certain way.[/LIST] [/LIST]Once your re-installation is complete, the usual thing to do would be to untar the old home directory *before* logging in as that user for the first time. In theory, as you reinstall all your old applications, they should pick up (and perform any necessary upgrades on) all the old personal settings. However, I strongly suggest _not deleting the original tarball for at least a week_ ... just in case something goes wrong, and you need to **sudo rm -R /home/username** and start again!

Personally, I loathe re-installations (and almost never do them), but like you, I tend to prefer a clean slate when performing significant upgrades. I hope this helps you make a smooth transition!

[SIZE=1]**Edit:** It is worth noting that many users (myself included) habitually store /home on a separate partition. In theory (again!) this practice can make OS re-installations quick and painless, because all user-specific data simply stays put and (in theory!) ports directly from one install to the next, without intervention. When installing Feisty, you might like to consider this option.[/SIZE]

---

