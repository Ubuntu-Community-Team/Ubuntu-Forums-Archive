---
title: "installing minimal"
date: 2008-04-11
forum: Installation &amp; Upgrades
---

### Post by skeetwood-mac on 2008-04-11
I installed minimal but theres no graphic desktop. do I need gnome? how do I get that just from the text mode? ugh I've been trying to install ubuntu for the last couple days and I'm so close!

---

### Post by kerry_s on 2008-04-11
from the minimal:
full ubuntu->
sudo apt-get install ubuntu-desktop

for lighter->
sudo apt-get install xorg gdm fluxbox
reboot

---

### Post by skeetwood-mac on 2008-04-11
alright I tried that and it installed for a while then I got some parser error that said premature end of data. I rebooted and tried it again and it said E: dpkg interupt manually run "dpkg --configure -a" so I did and it installed some more then I got the parser error again.

---

### Post by kerry_s on 2008-04-11
sounds like your internet is cutting out on you.

---

### Post by skeetwood-mac on 2008-04-11
hmm I dont know I tried it again and it won't get passed "diveintopython"

it says 

/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:653: parser error


and it also says premature end of data in tag  a couple times

---

### Post by kerry_s on 2008-04-11
parser error that's usually cache.
run> sudo apt-get update

what are your specs it sounds like your running out of memory.

---

### Post by skeetwood-mac on 2008-04-11
ah HA! Finally. Im writing this from ubuntu!!! I still got a couple of those parser errors but then it would keep going. then after it stopped I did startx and it started up. so I guess I&#314;l see how this goes. Thanks for the help!

---

### Post by skeetwood-mac on 2008-04-11
ahhh! Now I can´t update!? 

Failed to run /usr/sbin/synaptic '--hide-main-window' '--non-interactive' '--parent-window-id' '58720259' '--progress-str' 'Please wait, this can take some time.' '--finish-str' 'Update is complete' '--set-selections-file' '/tmp/tmpq_tj4-' as user root.

Unable to copy the user's Xauthorization file.

---

### Post by skeetwood-mac on 2008-04-11
oh nevermind  I managed to figure that out.

---

