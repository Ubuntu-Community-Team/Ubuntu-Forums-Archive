---
title: "how to list my program or package that i compile and installed"
date: 2011-06-26
forum: Installation &amp; Upgrades
---

### Post by jao_madn on 2011-06-26
Hi

I would like to ask in ubuntu or linux on how to list all my package or software the i installed via source code( compile installed in dir default is /usr/local) just like i solaris in which if you installed a package in ur choosing default root installation dir you can just issue a command pkginfo -l -R < any root dir you installed the package>.

I have no luck in dpkg and apt-get. or there no such command that will check the packages install in the /usr/local.

---

### Post by Bachstelze on 2011-06-26
If you can't keep track of the packages you installed from source, you probably shouldn't do it. What's wrong with the packages from the repositories? Also look into checkinstall.

---

### Post by Enigmapond on 2011-06-26
> **Bachstelze said:**
> If you can't keep track of the packages you installed from source, you probably shouldn't do it. What's wrong with the packages from the repositories? Also look into checkinstall.

I agree with this as everything I install from source goes in /opt or in my home directory in a bin file I created.

---

### Post by jao_madn on 2011-06-26
> **Bachstelze said:**
> If you can't keep track of the packages you installed from source, you probably shouldn't do it. What's wrong with the packages from the repositories? Also look into checkinstall.

@Bachstelze: Sometimes there are software that i primary used have some bugs or functionality missing or issue that can be annoying and cant wait for the latest version for the LTS distro i had.

---

### Post by Bachstelze on 2011-06-26
Then checkinstall will help you. Basically it creates a DEB package with your compiled software, so you can manage it later using the standard Apt/dpkg tools. Also, if you use a lot of compiled software, maybe you should consider switching to Gentoo or Arch.

---

### Post by jao_madn on 2011-06-26
> **Bachstelze said:**
> Then checkinstall will help you. Basically it creates a DEB package with your compiled software, so you can manage it later using the standard Apt/dpkg tools. Also, if you use a lot of compiled software, maybe you should consider switching to Gentoo or Arch.

@Bachstelze: Thanks for the input, may i ask if i may: why you recomment or maybe you can provide some additional info on why or how the switching to gentoo or arch if someone using a lot of compile software from source code. By the way thanks..

---

