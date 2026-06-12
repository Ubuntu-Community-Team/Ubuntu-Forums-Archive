---
title: "System in restart loop."
date: 2006-08-09
forum: Installation &amp; Upgrades
---

### Post by Kodai on 2006-08-09
I just finished installing  ubuntu-6.06-server-i386. installing went well, easy. I installed light. Then after it installed, it started the grub, went to the booting, and then just restarts. I thought maybe I needed to install the hd version. It does the EXACT same thing. I tried going into safe mode, but that did us no good, because it restarts too. Please help.

---

### Post by Kodai on 2006-08-09
> **Kodai said:**
> I just finished installing  ubuntu-6.06-server-i386. installing went well, easy. I installed light. Then after it installed, it started the grub, went to the booting, and then just restarts. I thought maybe I needed to install the hd version. It does the EXACT same thing. I tried going into safe mode, but that did us no good, because it restarts too. Please help.

bump >.< c'mon guys ;_; I'd really like this to work..

---

### Post by tacoman on 2006-08-29
same problem here it goes thru the little os selction menu in grub it selects the server one and when its loading it gets to 
boot:
and just restarts with no warning

---

### Post by confused57 on 2006-08-29
There's a bug with the server installation cd and certain hardware that causes this problem...I had the continuous reboot with an AMD K6-2 500 MHz processor, but worked fine on a computer running an Intel P4 2.0 GHz.  It's a problem I've seen reported by several posters, most running a system similar to the first one I mentioned.
   You can install a server using the Dapper alternate cd, which worked for me on the AMD machine.

---

### Post by donburch on 2006-11-02
> **confused57 said:**
> There's a bug with the server installation cd and certain hardware that causes this problem...I had the continuous reboot with an AMD K6-2 500 MHz processor, but worked fine on a computer running an Intel P4 2.0 GHz.  It's a problem I've seen reported by several posters, most running a system similar to the first one I mentioned.
   You can install a server using the Dapper alternate cd, which worked for me on the AMD machine.

Same with 6.10   :-(  

Pity that we can't run Ubuntu server on an older machine, like my AND K6-2 @ 300MHz.  I'm wanting to upgrade from a 200MHz PC with Win2K running IIS and email servers. 

Strangely the Alternate and Desktop do run OK ... it's only the server version that reboots immediately after selecting the OS.

---

### Post by slickrb on 2006-11-02
I am also haveing the same problem on an AMD k6 pc.  Can you set up a lamp server using the Alternate install CD?

---

### Post by slickrb on 2006-11-03
I have also tested a fresh install of Edgy 6.10 server and it has the same bug.  Not sure how to get this reported?

---

### Post by donburch on 2006-11-04
This *has* been reported, but it's a devil of a job to find it in the search functions on the bug site :-(  

Apparently it's considered unimportant ... probably because no-one in their right mind would want to use an old machine for a linux server ;)  

Instead, the work around is to use the Alternate install, then install Apache, MySQL and PHP5 - none of which are in the standard Ubuntu repositories - then configure them, and finally apply any security patches.  And if you succeed, you're no longer a noob ! 

Personally I am taking the easier option ... building a 2GHz Celeron (around a left-over CPU) and install XP Professional. Or having built a new machine specially I guess I could try the Ubuntu LAMP server install.  

My opinion is that Ubuntu is easy to use - when everything goes OK - but any setback forces the user into the HUGE unix learning curve - which is the reason people have been put off unix/linux for over 20 years.  I think effort should be going into making the error and recovery process more user-friendly for non-gurus, rather than porting even more packages (which serves to confuse new users).

---

