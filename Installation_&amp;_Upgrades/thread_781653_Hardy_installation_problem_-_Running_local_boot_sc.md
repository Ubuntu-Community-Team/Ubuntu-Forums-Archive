---
title: "Hardy installation problem - Running local boot scripts (/etc/rc.local)"
date: 2008-05-04
forum: Installation &amp; Upgrades
---

### Post by dannyboy1121 on 2008-05-04
Folks .. whilst attempting to get Hardy to run from the live CD it hangs at:

"Running local boot scripts (/etc/rc.local) [OK]"

Hitting ctrl-alt and F2 takes it to command line.

Try to kick start X using startx and it fails with the following errors:

unable to connect to xserver
fatal server error
no screens found
vesa: no matching modes

(not in that order).

So it appears that there is no monitor support for my laptop?

Model : [http://www.samsung.com/he/products/notebookcomputer/r_series/np_r40plus.asp](http://www.samsung.com/he/products/notebookcomputer/r_series/np_r40plus.asp)

Any ideas how I can get round this? Help appreciated. :-/

---

### Post by lemming465 on 2008-05-05
If you aren't getting any video, but do have command live virtual terminal access, you can look in /var/log/Xorg.0.log and try to find out what the relevent error message is.

If Ubuntu Hardy isn't working for you, try Ubuntu Gutsy 7.10 and see if that does any better.  Or try Fedora or OpenSuSE.  Ubuntu 8.04 went for autoconfigured X in a big way, which is great for most people, but is having some teething troubles on more esoteric hardware.

---

### Post by PmDematagoda on 2008-05-05
What you are having is an X-Server configuration error, did you try rebooting Ubuntu in Recovery Mode and then reconfiguring the X-Server to it's defaults by executing:-
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
and then starting the X-Server with:-
```
startx
```

Edit:- Whoops, you already did, sorry. Unfortunately I may not be able to help much since I am not really good with ATi cards, so you may want to wait until someone who is competent with ATi cards comes along.

---

