---
title: "Where does apt install libraries to?"
date: 2023-03-27
forum: Installation &amp; Upgrades
---

### Post by vilthivus on 2023-03-27
I just installed[FONT=monospace][COLOR=#000000] libblas64-3[/COLOR] [/FONT][FONT=monospace]using [/FONT]```
[FONT=monospace][COLOR=#000000]apt install libblas64-3[/COLOR][/FONT]
```[FONT=monospace] but now I cannot find where the *.so file resides. Shouldn't it usually be under /usr/lib? I looked there and I found that this directory contains mostly folders with barely any lib*.so files. Where are all the libraries that I installed and that came with the distribution?

And while we are on it, since I am new Ubuntu user, I was confused when I found on this [link]("https://help.ubuntu.com/stable/ubuntu-help/addremove-install.html.en") the way to install software is very different from the one I often encountered from online tutorials and guides, which is using ```
apt install
``` or ```
apt-get
```. What's the most mainstream way to install and manage packages in Ubuntu?
[/FONT]

---

### Post by guiverc on 2023-03-27
You didn't provide any release details; but packages install to the directories that packager set them to install to; which can vary on release.

Online you can view details at packages.ubuntu.com, which for **my** release will point to [https://packages.ubuntu.com/lunar/libblas64-3](https://packages.ubuntu.com/lunar/libblas64-3)

On viewing the *amd64* link (*my architecture*) that will send you to this page - [https://packages.ubuntu.com/lunar/amd64/libblas64-3/filelist](https://packages.ubuntu.com/lunar/amd64/libblas64-3/filelist), ie. the *lunar* package for *amd64* installs
```

/usr/lib/x86_64-linux-gnu/blas64/libblas64.so.3
/usr/lib/x86_64-linux-gnu/blas64/libblas64.so.3.11.0
/usr/share/doc/libblas64-3/changelog.Debian.gz
/usr/share/doc/libblas64-3/copyright
/usr/share/lintian/overrides/libblas64-3

```

You can also view this detail from cli, eg. `apt-file show libblas64-3` ... but be aware your system may **not** use these files or directories as that detail is release specific (*even though for most packages/architectures it's the same*) and you didn't provide OS/release details.

As for `apt` or `apt-get`....   Apt is the new replacement tool that may replace the older `apt-get` tool...   Both exist on most releases, as there are still some (*rarely used*) options that `apt-get` can perform that `apt` cannot yet do.   For 99.7% of cases though; `apt` is generally superior. I'd expect `apt-get` to become *deprecated* once the .3% is catered for (*whenever that is*).

---

### Post by vilthivus on 2023-03-27
Thank you so much for the useful information. Knowing that packages.ubuntu.com exists is really helpful. 
My Ubuntu version 20.04 focal.

---

### Post by mIk3_08 on 2023-03-27
> **vilthivus said:**
> Thank you so much for the useful information. Knowing that packages.ubuntu.com exists is really helpful. 
My Ubuntu version 20.04 focal.
On how to mark this thread as solve,
Please Click the "Solve thread" link below. Regards and cheers.

---

