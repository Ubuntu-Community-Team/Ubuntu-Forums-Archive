---
title: "[SOLVED] Can't boot - ends ub at &amp;quot;grub&amp;gt;&amp;quot;. Please help"
date: 2008-07-06
forum: Installation &amp; Upgrades
---

### Post by neilg4rqn on 2008-07-06
Hi, I was trying to ensure that I had updated to 8.04.1 and read in a thread I now cannot find (as I am now using my windoze box)that I should update this and that and then enter a command that I cannot quite remember but had something to do with the boot file. When I try to boot that machine now all I get is some text starting"[minimal Bash-like editing" etc etc. which leaves me completely stuck.
My Ubuntu system is the only one on that machine and all partitions are as default, there is no MSoft setup on it in any form.
Please can you tell me how to get back to where I was?
My feeling is that I have broken /boot/grub/menu.lst which I cannot find - only menu.1st~ and a couple of other variations on the suffix. These I found by booting from the 'live' cd but I cannot appear to get root privelages in that condition.
I have a 'custoom live cd' which I made and a 'recovery' cd which I can't figure out how to use.
Neil

---

### Post by overdrank on 2008-07-06
> **neilg4rqn said:**
> Hi, I was trying to ensure that I had updated to 8.04.1 and read in a thread I now cannot find (as I am now using my windoze box)that I should update this and that and then enter a command that I cannot quite remember but had something to do with the boot file. When I try to boot that machine now all I get is some text starting"[minimal Bash-like editing" etc etc. which leaves me completely stuck.
My Ubuntu system is the only one on that machine and all partitions are as default, there is no MSoft setup on it in any form.
Please can you tell me how to get back to where I was?
My feeling is that I have broken /boot/grub/menu.1st which I cannot find - only menu.1st~ and a couple of other variations on the suffix. These I found by booting from the 'live' cd but I cannot appear to get root privelages in that condition.
I have a 'custoom live cd' which I made and a 'recovery' cd which I can't figure out how to use.
Neil

Hi and it is not menu.1st but ```
gksu gedit /boot/grub/menu.lst
```
That is a small L not a 1

---

### Post by neilg4rqn on 2008-07-06
Thank you very much Overdrank. The line that you sent pointed me in the right direction. For the benefit of anyone else who has this problem here is what I did.

1 Boot from my CustomLiveCD (make one it's worth it)
2 Make a user (I used my original username/password) who will be able to use commends like "su root"
3 Open a terminal and type in "gksu gedit /boot/grub/menu.lst" as suggested by Overdrank.
4 The file that opened in gedit was blank so I drag/dropped menu.lst.backup from /boot/grub/ and saved it as menu.lst (note LST in lower case NOT 1st)
5 Boot from cold.
6 Make note to have large single malt later.

---

