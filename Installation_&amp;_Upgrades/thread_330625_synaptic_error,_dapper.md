---
title: "synaptic error, dapper"
date: 2007-01-03
forum: Installation &amp; Upgrades
---

### Post by zappj on 2007-01-03
Ubuntu Linux newbie.

Installed dapper fine everything works. When I use Synaptic Package Manager I get the following error      W: GPG error: [http://ubuntu.uni-klu.ac.at](http://ubuntu.uni-klu.ac.at) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 84F27CD6A2BF7BCB.  How do I fix this??  Also never used command line before and i would really like to install flashplayer 7. Any help with very simplified steps, directions (as you would a small child) would sure be great. Thanks

---

### Post by loserboy on 2007-01-03
it's not advertised on the forums much anymore but a great program to try would be automatix.
[www.getautomatix.com](www.getautomatix.com)

theres easy instructions on the website, it basically will automatically setup flash, and codecs and all sorts of cool stuff, i suggest you try it.
lemme know how it turns out.

---

### Post by arnieboy on 2007-01-03
> **zappj said:**
> Ubuntu Linux newbie.

Installed dapper fine everything works. When I use Synaptic Package Manager I get the following error      W: GPG error: [http://ubuntu.uni-klu.ac.at](http://ubuntu.uni-klu.ac.at) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 84F27CD6A2BF7BCB.  How do I fix this??  Also never used command line before and i would really like to install flashplayer 7. Any help with very simplified steps, directions (as you would a small child) would sure be great. Thanks
This error is coming from a third party repository that you added. 
There could be two reasons:
1) You did not add the correct GPG key for the repository (go to the website where you got information about this repo and check how you can add the correct key)
2) You have already added the key but the repository itself has been incorrectly updated recently. This error should be fixed in their next update if they are aware of it.

---

### Post by zappj on 2007-01-03
Thanks for the link it worked awesome. I appreciate your help. Thanks again.

---

### Post by loserboy on 2007-01-03
np, in the future its prolly best to try to learn how to do things without automatix, but from one noob to another its a sweet way to get stuff setup that you need then get ur hands dirty with optional stuff.

---

### Post by zappj on 2007-01-03
So, will I get this error if I, through ignorance or enthusiasm, hit enter too many times or try to install it again?

---

### Post by loserboy on 2007-01-05
um.... thats over my head but, i think the only reason you got the error is because you either didnt enter the right GPG key or none at all (i dont exactly know what a GPG is but its something along the lines of when you go to download something from the repo the key tells the server its ok for u to download)

> 
1) You did not add the correct GPG key for the repository (go to the website where you got information about this repo and check how you can add the correct key)
2) You have already added the key but the repository itself has been incorrectly updated recently. This error should be fixed in their next update if they are aware of it.

---

