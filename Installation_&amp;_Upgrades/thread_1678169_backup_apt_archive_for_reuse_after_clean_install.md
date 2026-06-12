---
title: "backup apt archive for reuse after clean install"
date: 2011-01-29
forum: Installation &amp; Upgrades
---

### Post by xannaxprozaxx on 2011-01-29
Hello;
I am really sorry if this has been posted before. I searched and could not find something that is precisely related to my problem.
Here it is:
I do several things, involving a lot of different software (coding, image manipulation, drawing, video editing, etc).
And where I live, internet is utterly slow, so instead of actually benefiting of the quick Ubuntu install, I am doomed to spend countless days re-downloading my packages each time.
Before my last format, having gained a slightly greater understanding of how Linux works, I saved all the content of apt archives, so synaptic would pick the packages already downloaded from there.
But it does not! It re-downloads every package.
What should I do to have synaptic recognize packages that are already there?

Note: I am NOT looking to create a mirror repository, aptOnCd and whatnot. I also DO NOT want to install packages by hand, one by one or all together.
All these solutions are certainly valuable (and I've tried a good bunch of them), but then I have to update manually my mirrored repository and/or install updates manually. Furthermore, it leaves me with two directories with packages, apt archive and ~/my-repository, which is just messy (in my view at least).
Any suggestion?

---

### Post by zvacet on 2011-02-01
I don´t understand why aptoncd is not solution for you,but you can do same thing other way.Copy content of /var/cache/apt/archives to new folder (give that new folder name what ever you want).Save that folder on external drive or separate home if you have it.After new install put that folder in your home directory and go inside of it ( let say new folder name id **newfol**) 

```
cd newfol
```

and then 

```
sudo dpkg -i *deb
```

That will install all deb packages.

---

