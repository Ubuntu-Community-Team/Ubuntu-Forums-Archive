---
title: "Where's DIR_COLORS?"
date: 2006-06-24
forum: Installation &amp; Upgrades
---

### Post by minkoo.seo@gmail.com on 2006-06-24
Hi all.

I'd like to change colors when I run ls and I want that to be global. Global means that I want to change colors of every singlue user. In case of Fedora, I could do that with /etc/DIR_COLORS. In Ubuntu, there's no /etc/DIR_COLORS. That being the case, how can I change colors globally?

Should I have to touch every .bashrc or .bash_profile of every user?

Sincerely,
Minkoo Seo

---

### Post by jrib on 2006-06-24
man dir_colors seems to indicate ubuntu doesn't use /etc/DIR_COLORs

You could just set LS_COLORS in /etc/profile and /etc/bash.bashrc

---

### Post by minkoo.seo@gmail.com on 2006-06-24
This is strange because Ubuntu provides with some colors though it has no configuration file. How can it be possible? Are there no configuration file but ls is  coloring by itself?

[QUOTE=_jason]man dir_colors seems to indicate ubuntu doesn't use /etc/DIR_COLORs

You could just set LS_COLORS in /etc/profile and /etc/bash.bashrc[/QUOTE]

---

### Post by jrib on 2006-07-04
[QUOTE=minkoo.seo@gmail.com]This is strange because Ubuntu provides with some colors though it has no configuration file. How can it be possible? Are there no configuration file but ls is  coloring by itself?[/QUOTE]

my ~/.bashrc has `dircolors -b`, that seems to be setting the colors here.  That's there as default I believe, since it is also in /etc/skel/.bashrc .

---

### Post by Shack on 2007-09-02
I have same kind of problem.

When using nutty or putty I'm having my directories as blue on black background and you can image what that looks like.

I would like to change my directories yellow but I haven't been able to change it.

Is there configuration file somewhere for dircolors? Or how can I change my directory colors?

---

