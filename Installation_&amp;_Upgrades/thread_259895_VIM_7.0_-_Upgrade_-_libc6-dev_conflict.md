---
title: "VIM 7.0 - Upgrade - libc6-dev conflict"
date: 2006-09-18
forum: Installation &amp; Upgrades
---

### Post by niravdani on 2006-09-18
First, I am new to Ubuntu : Just for my konwledge : What's Dapper, edgy, brezy? And how do I find out which one is my installation?

Ok, to question.

sudo apt-get remove --purge vim  : done
---------------------------------------
Installing VIM 7.0 gives dependencies problem on libc6-dev module.
Any idea how to handle this?
------------------------------------------------------------
gdebi the followings

vim-full_7.0-0.35+lubuntu4_all.deb depends on, so installed  
vim-common_7.0-0.35+lubuntu4_i386.deb, depends on, so installed
libc6_2.3.6-0ubuntu20_i386.deb gives conflict on 
libc6-dev_2.3.6-0ubuntu20_i386.deb

ofcourse, "apt-get install vim" installs back 6.4, so no point there

also tried updating sources.list with 
"deb http://www.freshnet.org/dapper/vim/" and "deb http://www.freshnet.org/dapper/" - but synaptic download manager is not updated, rather it gives an error on connecting any of the other sources.

---

### Post by dante.regis on 2006-09-23
niravdani,

Sorry, but I can't help you with your vim7 question.

Regarding Breezy, Edge etc: it's the name given to each release of Ubuntu. The last one released (on June, 2006 - version 6.06) is Dapper Drake, or dapper. The next one will be Edgy (version 6.10). To know whitch version you are using, just go to the SYSTEM menu, on the top of your screen, and click on ABOUT UBUNTU.

Hope this is clear! Best

---

### Post by xolot1 on 2006-09-23
i have a similar problem trying to upgrade libc6.  hopefully someone can help us out.

---

