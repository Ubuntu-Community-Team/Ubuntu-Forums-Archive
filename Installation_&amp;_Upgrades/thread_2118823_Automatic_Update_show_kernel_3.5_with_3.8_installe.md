---
title: "Automatic Update show kernel 3.5 with 3.8 installed"
date: 2013-02-22
forum: Installation &amp; Upgrades
---

### Post by ubunet on 2013-02-22
Hi,

I have Xubuntu 12.10 x86 installed with kernel 3.8. I installed this kernel using a tutorial in a **[Liberian Geek]("http://www.google.com.br/url?sa=t&rct=j&q=&esrc=s&source=web&cd=2&cad=rja&ved=0CDYQFjAB&url=http%3A%2F%2Fwww.liberiangeek.net%2F2013%2F02%2Flinux-kernel-3-8-released-with-improved-graphic-drivers-and-new-filesystem-for-flash-drives%2F&ei=kWEnUZLxEpH89gSmqoHwAQ&usg=AFQjCNGCb6GZBOmN7jDE77j-cSMF_UtoqQ&bvm=bv.42768644,d.eWU")** site.

Now the "Automatic Updates" show kernel 3.5 to "update" (downgrade im my case). How I block kernel update if it is more lower than my actual kernel?

---

### Post by dino99 on 2013-02-22
as often said "ubuntu suppose user understanding what he do"  :p

if you follow some "geek" howto, outside the ubuntu wikis, then its at your own risk  ):P

ok, i'm stopping kidding  ;)

3.5 is the stock 12.10 kernel, so its normally updated
3.8 is updated due to your tweak (but you surely understand what you have done, do you ? ).

in fact that "geek" blog have proposed to install the "vanilla" kernel, meaning without the custom ubuntu settings, so if you glance at your logs (but surely you still do it right ?) you get a bunch of apparmor warnings.
if you want to get the latest kernel from ubuntu, then from synaptic, install linux-lts-raring package from that ppa:
[https://launchpad.net/~ubuntu-x-swat/+archive/r-lts-backport](https://launchpad.net/~ubuntu-x-swat/+archive/r-lts-backport)

---

### Post by ubunet on 2013-03-05
I installed kernel 3.5 and 3.8 still active. It's not a bug or issue. I don't knowed.

---

