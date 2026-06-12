---
title: "ubuntu core goes back to configure sequence after reboot"
date: 2020-03-06
forum: Installation &amp; Upgrades
---

### Post by ericsenn on 2020-03-06
hello,

I have installed and configure ubuntu core 16 on the Odroid XU4 board.
The wifi support was not working at first so I did achieve the "configure" sequence via a wired network connection.
Once finished, ubuntu core beeing installed, I sshed to my board and set the wifi connection to work (thanks so snap'in the network-manager).
Everything seems to work flawlessly but, when I reboot, the system ask again for a new "configure" sequence,
and I am not able to sshed until I comply with this new sequence (choosing a netework connection via my wifi).
After that I can ssh and operate the board, but the board goes back to the "press enter to configure" screen via its hdmi.
What can I do to record for once my board beeing configured and to be able to ssh directly once booted ?
Thank you for your help.

éric

ps: I have this problem and does not know where to post it, in fact I did not find a dedicated room for ubuntu core in this forum.

---

### Post by slickymaster on 2020-03-06
Thread moved to **Installation & Upgrades** for a better fit

---

### Post by ericsenn on 2020-03-06
I found a fix (but I'm not sure this is the better way ...) :
(inspired from the script found there [https://git.launchpad.net/~snappy-hwe-team/snappy-hwe-snaps/+git/tests-extras/tree/create-image-scripts/create-image.sh](https://git.launchpad.net/~snappy-hwe-team/snappy-hwe-snaps/+git/tests-extras/tree/create-image-scripts/create-image.sh))

cd /writable/system-data/var/lib/console-conf/
sudo touch complete

---

