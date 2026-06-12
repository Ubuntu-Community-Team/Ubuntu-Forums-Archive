---
title: "Dual Boot error (Minimal Bash) after updating"
date: 2015-11-20
forum: Installation &amp; Upgrades
---

### Post by tommaso4 on 2015-11-20
Hi everyone, after almost an year of Ubuntu, yesterday, while i was updating the system i run into a problem and the system rebooted and showed this:
> [COLOR=#000000][FONT=Ubuntu Mono] GNU GRUB version 1.98-1ubuntu5-1mint2[/FONT][/COLOR]

Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file completions.

grub>


I was able to solve the problem using a live version of Ubuntu and running the grub repair.
But today after i executed this command i got the same problem again.
```
sudo dpkg --configure -a

```

Now i think i can solve the problem again using a live USB of ubuntu and the grub repair but i would like to have a definitive fix since otherwise i can't update the system.


Thanks!

---

### Post by kansasnoob on 2015-11-21
When you say "grub repair" do you mean you've been using Boot Repair:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

If so the next time you use Boot Repair please post the link to the boot info summary.

Without more specific info I can only guess, but dpkg "remembers" prior grub configuration settings so each time dpkg runs it'll restore the previous "saved" settings even if those settings are wrong. So what I do after repairing grub and booting into the installed version of Ubuntu is run:

```
sudo dpkg-reconfigure grub-pc
```

Then I have to be certain to tell grub where it should be installed and any other non-default settings. Of course this works only for standard BIOS/MBR type installs. UEFI installs use a different version of grub so the package name is different, etc.

---

### Post by tommaso4 on 2015-11-21
Yes, i used that program!
And this is the link of the boot info summary [http://paste.ubuntu.com/13397055/](http://paste.ubuntu.com/13397055/)

Thanks!

EDIT: I tried to use that command but:
"dpkg-query: the packet "grub-pc" is not installed..."

---

