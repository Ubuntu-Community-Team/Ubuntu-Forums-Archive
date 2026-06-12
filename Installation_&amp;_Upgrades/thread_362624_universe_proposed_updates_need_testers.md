---
title: "universe proposed updates need testers"
date: 2007-02-15
forum: Installation &amp; Upgrades
---

### Post by StefanPotyra on 2007-02-15
Hi,

currently the following packages in universe or multiverse have a pending update. However to avoid breakage, we've settled upon the policy that five people need to test a package first, before it can enter the -updates repository. And that's where we need your help.

In order to test a proposed update, you'll need to add
*deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-proposed universe multiverse*
to test updates for **edgy** or

*deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-proposed universe multiverse*
to test updates for **dapper** to your */etc/apt/sources.list*.


If you test a package, please leave a comment to the referring bug, that the package works for you. Please also don't hesitate to comment on the bug if the package broke s.th.!

Here is a list of proposed updates for **edgy** (well, rather the bug links):
libnss-ldap
[https://launchpad.net/ubuntu/+source/libnss-ldap/+bug/70146](https://launchpad.net/ubuntu/+source/libnss-ldap/+bug/70146)

pouetchess
[https://launchpad.net/ubuntu/+source/pouetchess/+bug/72052](https://launchpad.net/ubuntu/+source/pouetchess/+bug/72052)

k3d
[https://launchpad.net/ubuntu/edgy/+source/k3d/+bug/64848](https://launchpad.net/ubuntu/edgy/+source/k3d/+bug/64848)

eclipse
[https://launchpad.net/ubuntu/+source/eclipse/+bug/68380](https://launchpad.net/ubuntu/+source/eclipse/+bug/68380)

gtetrinet
[https://launchpad.net/ubuntu/+source/gtetrinet/+bug/74133](https://launchpad.net/ubuntu/+source/gtetrinet/+bug/74133)

kxdocker
[https://launchpad.net/ubuntu/+source/kxdocker/+bug/74862](https://launchpad.net/ubuntu/+source/kxdocker/+bug/74862)

azureus
[https://launchpad.net/ubuntu/edgy/+source/azureus/+bug/42269](https://launchpad.net/ubuntu/edgy/+source/azureus/+bug/42269)

oprofile
[https://launchpad.net/ubuntu/+source/oprofile/+bug/69455](https://launchpad.net/ubuntu/+source/oprofile/+bug/69455)

xdg-utils
[https://launchpad.net/ubuntu/+source/xdg-utils/+bug/74408](https://launchpad.net/ubuntu/+source/xdg-utils/+bug/74408)

rpy
[https://launchpad.net/ubuntu/edgy/+source/rpy/+bug/70495](https://launchpad.net/ubuntu/edgy/+source/rpy/+bug/70495)

kiso
[https://launchpad.net/ubuntu/+source/kiso/+bug/75908](https://launchpad.net/ubuntu/+source/kiso/+bug/75908)

spampd
[https://launchpad.net/ubuntu/+source/spampd/+bug/76861](https://launchpad.net/ubuntu/+source/spampd/+bug/76861)

qpsmtpd
[https://launchpad.net/ubuntu/+source/qpsmtpd/+bug/77485](https://launchpad.net/ubuntu/+source/qpsmtpd/+bug/77485)

gnome-hearts
[https://launchpad.net/ubuntu/+source/gnome-hearts/+bug/79059](https://launchpad.net/ubuntu/+source/gnome-hearts/+bug/79059)

xmms-sid
[https://launchpad.net/ubuntu/+source/xmms-sid/+bug/82692](https://launchpad.net/ubuntu/+source/xmms-sid/+bug/82692)

idjc
[https://launchpad.net/ubuntu/+source/idjc/+bug/66475](https://launchpad.net/ubuntu/+source/idjc/+bug/66475)

And for **dapper**:
qpsmtpd
[https://launchpad.net/ubuntu/+source/qpsmtpd/+bug/78005](https://launchpad.net/ubuntu/+source/qpsmtpd/+bug/78005)

lighttpd
[https://launchpad.net/ubuntu/+source/lighttpd/+bug/59269](https://launchpad.net/ubuntu/+source/lighttpd/+bug/59269)

dosemu
[https://launchpad.net/ubuntu/+source/dosemu/+bug/72951](https://launchpad.net/ubuntu/+source/dosemu/+bug/72951)


P.S.: I'll try to update the list every two weeks. 

Thanks,
   Stefan aka sistpoty.

---

### Post by hod139 on 2007-02-16
I wouldn't mind helping out, but what are the chances of it breaking my system?  My laptop is running dapper, but I can't risk breaking that.  My desktop is running edgy, and aside from my girlfriend getting angry at me if it breaks, it is slightly less critical.

---

### Post by Kateikyoushi on 2007-02-18
I am using those repos for a while, I check the packages and post what I found.

---

### Post by PriceChild on 2007-02-20
> **hod139 said:**
> I wouldn't mind helping out, but what are the chances of it breaking my system?  My laptop is running dapper, but I can't risk breaking that.  My desktop is running edgy, and aside from my girlfriend getting angry at me if it breaks, it is slightly less critical.If you need your machines always running then don't add the repos just incase.

---

### Post by Kateikyoushi on 2007-02-20
Is it possible that kernel upgrades make it to these repos before going mainstream in the future ?

---

### Post by StefanPotyra on 2007-02-22
@hod139: The risk is pretty minimal if you only *selectively* install software from this repositories that you want to test. All changes did get reviewed to make sure that it won't break things, but this of course doesn't mean that no bad things can happen ;).
Generally I'd not advise anyone to use the -proposed repositories just like the normal repositories.

@Kateikyoushi: thanks, would be very cool if you could add a comment to the bug reports I linked to. 
IIRC kernel updates for stable releases will be put into -proposed repositories (main however, not universe/multiverse), though I'm not 100% sure about this. (Kernel is a special case for updates).

And here's another one for **edgy**:
kdbus
[https://launchpad.net/ubuntu/+source/kdbus/+bug/73780](https://launchpad.net/ubuntu/+source/kdbus/+bug/73780)

---

### Post by Artemis3 on 2007-04-22
Your list doesn't show it but update-manager 0.45.3 is in proposed. Installing this in edgy killed the upgrade to 7.04 button from update-manager. -c and -d do nothing, not good.

[https://bugs.launchpad.net/update-manager/+bug/108541](https://bugs.launchpad.net/update-manager/+bug/108541)

---

### Post by Recovering from MS. on 2007-12-17
I would be more than happy to help, except I'm a newbie (like I just installed for the first time today)  I have a spare comp I could start using for testing... {p-3  733 /w 256mb  20gb HD} 

The other problem might be I'm not sure what you are testing.
A little more info would be helpful.

---

### Post by markharding557 on 2007-12-31
would it be  acceptable to test these on ubuntu running in a vm like virtualbox?

---

### Post by ~LoKe on 2008-01-03
> **markharding557 said:**
> would it be  acceptable to test these on ubuntu running in a vm like virtualbox?

The environment is essentially the same, so I don't see why it wouldn't be OK.

---

