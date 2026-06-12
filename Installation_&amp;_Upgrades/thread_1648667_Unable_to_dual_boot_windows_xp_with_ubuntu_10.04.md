---
title: "Unable to dual boot windows xp with ubuntu 10.04"
date: 2010-12-19
forum: Installation &amp; Upgrades
---

### Post by jimmy8910 on 2010-12-19
I have two separate hard disks, one having ubuntu 10.04 and one having Windows XP.

I'm unable to get an option to choose from grub menu as to which operating system i want to boot into.

How do i fix this?

---

### Post by lmarmisa on 2010-12-19
> **jimmy8910 said:**
> I have two separate hard disks, one having ubuntu 10.04 and one having Windows XP.

I'm unable to get an option to choose from grub menu as to which operating system i want to boot into.

How do i fix this?

Please, type this command and post its output:

```

sudo update-grub

```

---

### Post by sikander3786 on 2010-12-19
And if update-grub as suggested above, doesn't list your Windows install, boot into Ubuntu and post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

That would let us take a look at your setup and thus help diagnose the problem.

While posting, click the # icon in post menu and paste your text in between the generated code tags.

---

### Post by jimmy8910 on 2010-12-19
@[]("http://ubuntuforums.org/member.php?u=955260")Imarmisa & @sikander3786

The sudo update-grub command worked and now i get the grub menu to select the os.

Thanks for the help :)

---

