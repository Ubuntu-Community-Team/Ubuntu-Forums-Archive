---
title: "Failed Ubuntu upgrade from 11.04 to 11.10"
date: 2012-01-29
forum: Installation &amp; Upgrades
---

### Post by Nikkhil on 2012-01-29
I was using 11.04 for quite some time. Recently I decided to upgrade to  11.10 when the Ubuntu upgrade dialog box started popping up. The  upgrade manager downloaded required packages and started upgrading  the packages. Machine inadvertently got switched off  when last  11 minutes were left to complete upgraded. Now when I try starting  Ubuntu the following (possibly scrambled) message is shown after the  usual Ubuntu 11.04 boot-up screen

-----------------------------------------------------------------------------------------------
Ubuntu 11.04
....*Starting bluetooth    [OK]
*PulseAudio configured for per-user sessions
                                   Ubuntu 11.04saned disabled; edit /etc/default/s
aned
     Rather than invoking init scri....*Checking battery state...[OK]
                                                                                            uti
lity,e.g. service S90binfmt-support start

           Since the script you are attempting to
invoke has been converted to an
  Upstart job, you may also use the start( 8 ) utili
ty, e.g. start S90binfmt-support
             Start: Unknown job:S90binfmt-support
    *Starting web server apache2   [OK}
-----------------------------------------------------------------------------------------------

I have dual installation (Windows as the primary and Ubuntu secondary  OS). I'm able to start Ubuntu in recovery mode. Wondering if using  commands I can finish the upgrade and start using 11.10 (or in worst  case 11.04) without loosing my data.

---

### Post by darkod on 2012-01-29
Are we talking about a laptop? How can a machine simply switch off?

Anyway, all unconfigured packages which were downloaded should be able to finish up with:

sudo dpkg --configure -a

---

### Post by Nikkhil on 2012-01-31
> **darkod said:**
> are we talking about a laptop? How can a machine simply switch off?

Anyway, all unconfigured packages which were downloaded should be able to finish up with:

Sudo dpkg --configure -a

:p Many thanks!!! Worked for me!

---

