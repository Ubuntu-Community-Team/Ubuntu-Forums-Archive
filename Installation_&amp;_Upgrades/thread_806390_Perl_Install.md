---
title: "Perl Install"
date: 2008-05-24
forum: Installation &amp; Upgrades
---

### Post by CyberCat7 on 2008-05-24
Hi,

I am a bit new to Ubuntu and I have a Bluetooth adapter that I can find no good use for (at the moment). anyhow, I want to play around with Bluesniff for a bit but I realise that I need to install Perl.

Can anybody walk me throught teh installation processs please?

I have Ububntu 8.04 with teh current updates installed (I upgraded from 7.10).

---

### Post by HalPomeranz on 2008-05-24
"sudo apt-get install perl" should do it.

---

### Post by Blacknole on 2011-03-05
I am also trying to play around with bluesniff. I have updated the perl library and installed curses yet get the following error: 

Can't locate Curses/Application.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.1 /usr/local/share/perl/5.10.1 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at ./bluesniff.pl line 23.
BEGIN failed--compilation aborted at ./bluesniff.pl line 23.

This is line 23

use Curses::Application;

---

