---
title: "&quot;kubuntu-desktop&quot; meta package - Help with the concept"
date: 2006-09-08
forum: Installation &amp; Upgrades
---

### Post by Bigglez on 2006-09-08
Hello,
First off, I am very happy with my Kubuntu 6.06 desktop, it's the  greatest O/S I have ever used.

I want to ask about this meta package "kubuntu-desktop". What I understand is that it is a kind of list of ingredients that go into a full Kubuntu installation. 
I gather one can apt-get remove it, and that does no harm, only removes the meta-package. 

I get a little confused at this point, because I wonder what happens later on, when it comes time for me to upgrade to a new Kubuntu version.

To exlain: I want to remove Amarok. Not because I don't like it, but because it's just slowing my machine too much. I have replaced it with xmms in every regard and so I want it gone.

Now, when I try to remove it from the command-line, it tells me "kubuntu-desktop" will also be removed. I could say "Y" and damn the consequences, but I want to know what they are.

If kubuntu-desktop is gone:
(1) On upgrade, will this cause a crisis?
(2) On installation of some other package that requires is, will it re-install it *and* all the apps it points to? Thus I would get Amarok back again, for example?
(3) On upgrade, would it want to do the same (2), re-install it and all it's components?

I hope you can see where my confusion lies, perhaps there is a resource I can visit to discover more about this. My searches have not been fruitful so far.

Thanks.

---

### Post by aysiu on 2006-09-08
> **Bigglez said:**
> 
If kubuntu-desktop is gone:
(1) On upgrade, will this cause a crisis? No, but when you upgrade to Edgy, you won't get any packages added or removed. You'll just get newer versions of the packages you already have installed.
> (2) On installation of some other package that requires is, will it re-install it *and* all the apps it points to? Thus I would get Amarok back again, for example? If you don't have *kubuntu-desktop* installed, AmaroK will stay uninstalled.
> (3) On upgrade, would it want to do the same (2), re-install it and all it's components? No.

In order to make a proper transition from Dapper to Edgy or from Edgy to Edgy+1, you'll need to have *kubuntu-desktop* installed. New versions of Ubuntu are not merely newer versions of the packages you already have installed. Sometimes packages are added or some packages are replaced with other packages.

---

### Post by Bigglez on 2006-09-08
Thanks for the info :)

Can I remove Amarok, and then re-install kubuntu-desktop?
That way I can do this everytime I want to change something that includes the meta package. For example I also want to get rid of the Kblue tooth stuff, which affects kubuntu-desktop.

Thanks.

---

### Post by aysiu on 2006-09-08
Unless you're hard up for disk space, I'd say just keep *kubuntu-desktop* installed. You can remove menu entries and launchers for AmaroK, and you can turn off the Bluetooth services.

---

### Post by Bigglez on 2006-09-09
Hi, sorry - I didn't get an email, so I forgot to check the thread.

Sounds like I better keep that package.

Pity I must keep on updating amarok and other apps that I never use.

I **really** would like to know more about the implications and concept of the kubuntu-desktop package. Does anyone know the best place I could go to start looking?

---

### Post by aysiu on 2006-09-09
Well, if you don't mind maintaining your own system and choosing your own packages, you can just leave *kubuntu-desktop* out. Honestly, though, the extra apps don't take up that much space. And, if you're not on dial-up (are you?), the extra download time for those unwanted apps is negligible.

---

### Post by Bigglez on 2006-09-10
aysiu - thanks for your help. I think I'll leave it in place until I learn more.

ciao
:D

---

### Post by aysiu on 2006-09-10
If you do learn more, please post your findings back here. Perhaps we can all stand to understand these metapackages a little better.

---

