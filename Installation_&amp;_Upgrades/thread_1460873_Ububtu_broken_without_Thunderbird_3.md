---
title: "Ububtu broken without Thunderbird 3"
date: 2010-04-23
forum: Installation &amp; Upgrades
---

### Post by Rebelli0us on 2010-04-23
I've been sharing my TB profile between Ubuntu & Windows. Then TB-windows updated to version 3, but TB-Ubuntu didn't, and vesions 2 and 3 are incompatible when sharing profile -- version 2 is unable to read v3 account settings and therefore cannot fetch mail! Evolution won't share and is unable to import 'settings'.. so Ubu OS is unusable without email...

Can we please have TB version 3 !!!



PS: I tried "A Single Command to Install Thunderbird 3 in Ubuntu":

[http://www.kabatology.com/12/09/a-single-command-to-install-thunderbird-3-in-ubuntu/](http://www.kabatology.com/12/09/a-single-command-to-install-thunderbird-3-in-ubuntu/)

Ran this in terminal:

wget -O - [http://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/latest-3.0/linux-i686/en-US/thunderbird-3.0.4.tar.bz2](http://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/latest-3.0/linux-i686/en-US/thunderbird-3.0.4.tar.bz2) | tar xj -C ~

It downloaded but didn't install anything, and I can't even find the file. Where is it? Search turns up nothing. Why is it so hard installing stuff in Ubu?!

---

### Post by bowens44 on 2010-04-23
add the PPA 
[https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa)

---

### Post by Rebelli0us on 2010-04-26
Thank you, than worked. After the PPA thing (whatever it means) I had to go to "Ubuntu Software Center" to actually install 3.0. The only problem, instead of thunderbird the app is now called Shredder! BUt it works and fetches mail.

Clean up:
The wget command in my original post fetched some file, (thunderbird-3.0.4.tar.bz2) that I'd like to find and delete... but I can't find it. Where is it?

---

