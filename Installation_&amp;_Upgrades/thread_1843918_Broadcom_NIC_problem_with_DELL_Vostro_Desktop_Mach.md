---
title: "Broadcom NIC problem with DELL Vostro Desktop Machine"
date: 2011-09-14
forum: Installation &amp; Upgrades
---

### Post by praveenksubedar on 2011-09-14
Hello friends, I have installed ubuntu 8.10 on my dell vostro desktop everything is working fine except network. I am unable to setup network as card has been detected but there is no drivers are installed. I dont know how i can solve this problem its very urgent so please help me:confused:

---

### Post by coffeecat on 2011-09-14
Welcome to the forum, praveenksubedar.

The first thing to say is that 8.10 is a very old release, unsupported for about 18 months now. Did you have a particular reason for installing such an old version? 

I suggest you install the long-term support 10.04 version, which has another 19 months of support on the desktop, or the latest 11.04 which will supported for a little over a year yet. You can download the ISOs for both those releases from here:

[http://www.ubuntu.com/](http://www.ubuntu.com/)

If you need help preparing an installation CD or USB, post back.

Once you have a later version of Ubuntu running, you should be able to install the appropriate Broadcom driver using the procedures described on this community documentation page:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by praveenksubedar on 2011-09-15
thanks for the reply coffeecat, there is no specific reason to install that version anyway i have installed ubuntu 11.04 now its working fine but there is also one more problem with that if u know the solution then let me know...
          After installation it has taken auto etho and working but i catn access my windows network. if i edit vpn connection then am able to access windows network places but unable to access internet. If u know the solution plz help me

---

### Post by coffeecat on 2011-09-15
I'm glad 10.04 solved your wireless problem.

By Windows network, I guess you mean accessing samba (Windows) shares. VPN (virtual private network) is not the way to go over your own home network. I suggest you start a new thread with a descriptive title because you need help from people with experience of Windows shares.

Good luck!

---

