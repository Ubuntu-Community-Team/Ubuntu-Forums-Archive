---
title: "having errors with postgresql update"
date: 2007-09-30
forum: Installation &amp; Upgrades
---

### Post by flawedprefect on 2007-09-30
I ran updates recently, but a thing called "postgresql-8.2" keeps giving me errors. I would leave it unchecke,d except every time I try and install something new, I still get this error:

E: /var/cache/apt/archives/postgresql-8.1_8.1.8-1ubuntu3_i386.deb: subprocess new pre-removal script returned error exit status 1
E: /var/cache/apt/archives/postgresql-8.2_8.2.5-0ubuntu0.7.04.1_i386.deb: subprocess new pre-removal script returned error exit status 1

Has anyone experienced this problem? Synaptic also gave me an error; furthermore, when I tried to uninstall, I got a warning that told me the package was badly damaged and I should... (it didn't finish the sentence).

Is postgresql something I vitally need? Is it easy to remove completely, if all else fails? Is there somewhere where I can source a stable package and compile it somehow?

I appreciate any help in advance.

---

### Post by Seisen on 2007-09-30
If you don't use SQL for database management then no you don't need it. To fix your problem do this in the terminal

```
cd /var/cache/apt/archives/
ls | less 
```

then find the package(s) causing the problem then do this

```
sudo rm packagename.deb
```

---

### Post by flawedprefect on 2007-09-30
thanks for the help. I think I know what I am doing (rm means remove?) but just in case, I am posting a print out of what the first command gives me:

> amarok_2%3a1.4.7-0ubuntu1~feisty1_i386.deb
amarok-xine_2%3a1.4.7-0ubuntu1~feisty1_i386.deb
app-install-data-commercial_7.3_all.deb
blender_2.44-2~feisty1_i386.deb
camorama_0.18-0ubuntu1_i386.deb
ekiga_2.0.3-0ubuntu8_i386.deb
evolution-exchange_2.10.1-0ubuntu1_i386.deb
evolution-plugins_2.10.1-0ubuntu2_i386.deb
fftw3_3.1.2-1build1_i386.deb
gtkam_0.1.14-0ubuntu1_i386.deb
k3b_1.0.3-0ubuntu3~feisty1_i386.deb
kdebase-bin_4%3a3.5.6-0ubuntu20.4_i386.deb
kdebase-data_4%3a3.5.6-0ubuntu20.4_all.deb
kdebase-kio-plugins_4%3a3.5.6-0ubuntu20.4_i386.deb
kdesktop_4%3a3.5.6-0ubuntu20.4_i386.deb
kicker_4%3a3.5.6-0ubuntu20.4_i386.deb
libauthen-pam-perl_0.16-1_i386.deb
libexif-gtk5_0.3.5-3_i386.deb
libifp4_1.0.0.2-3_i386.deb
libio-pty-perl_1%3a1.05-2build1_i386.deb
libk3b2_1.0.3-0ubuntu3~feisty1_i386.deb
libk3b2-mp3_1.0.3-0ubuntu3~feisty1_i386.deb
libkonq4_4%3a3.5.6-0ubuntu20.4_i386.deb
libkrb53_1.4.4-5ubuntu3.3_i386.deb
libmd5-perl_2.03-1_all.deb
libmtp5_0.1.3-0ubuntu2_i386.deb
libmysqlclient15off_5.0.38-0ubuntu1_i386.deb
libnet-ssleay-perl_1.30-1_i386.deb
libnjb5_2.2.5-4.1ubuntu2_i386.deb
libofa0_0.9.3-1_i386.deb
libpq4_8.1.8-1ubuntu3_i386.deb
libpq5_8.2.5-0ubuntu0.7.04.1_i386.deb
libqt3-headers_3%3a3.3.8really3.3.7-0ubuntu5.2_i386.deb
libqt3-mt_3%3a3.3.8really3.3.7-0ubuntu5.2_i386.deb
libqt3-mt-dev_3%3a3.3.8really3.3.7-0ubuntu5.2_i386.deb
libruby1.8_1.8.5-4ubuntu2_i386.deb
libssl0.9.8_0.9.8c-4ubuntu0.1_i386.deb
libssl-dev_0.9.8c-4ubuntu0.1_i386.deb
libt1-5_5.1.0-2ubuntu0.7.04.1_i386.deb
libtunepimp5_0.5.2-1ubuntu3_i386.deb
libwrap0_7.6.dbs-11ubuntu0.1_i386.deb
libxine-extracodecs_1.1.4-2ubuntu3_all.deb
libxvidcore4_2%3a1.1.2-0.1ubuntu1.1_i386.deb
libzvbi0_0.2.22-1_i386.deb
libzvbi-common_0.2.22-1_all.deb
linux-headers-2.6.20-16_2.6.20-16.32_i386.deb
linux-headers-2.6.20-16-generic_2.6.20-16.32_i386.deb
linux-image-2.6.20-15-generic_2.6.20-15.27_i386.deb
linux-image-2.6.20-16-generic_2.6.20-16.32_i386.deb
linux-libc-dev_2.6.20-16.32_i386.deb
linux-restricted-modules-2.6.20-15-generic_2.6.20.5-15.20_i386.deb
lock
module-assistant_0.10.10_all.deb
mysql-common_5.0.38-0ubuntu1_all.deb
nvidia-glx_1%3a1.0.9631+2.6.20.5-16.29_i386.deb
openssl_0.9.8c-4ubuntu0.1_i386.deb
ov511-source_2.32-3_all.deb
partial
pia_3.95.dfsg.1-2ubuntu1_i386.deb
postgresql-8.1_8.1.8-1ubuntu3_i386.deb
postgresql-client-8.1_8.1.8-1ubuntu3_i386.deb
python2.4_2.4.4-2ubuntu7_i386.deb
python2.4-minimal_2.4.4-2ubuntu7_i386.deb
qc-usb-utils_0.6.6-1_i386.deb
qt3-dev-tools_3%3a3.3.8really3.3.7-0ubuntu5.2_i386.deb
rhythmbox_0.10.0-0ubuntu2_i386.deb
ruby1.8_1.8.5-4ubuntu2_i386.deb
ruby_1.8.2-1_all.deb
samba_3.0.24-2ubuntu1.2_i386.deb
scantv_3.95.dfsg.1-2ubuntu1_i386.deb
tar_1.16-2ubuntu0.1_i386.deb
update-manager_1%3a0.59.25_all.deb
update-manager-core_1%3a0.59.25_i386.deb
vim-common_1%3a7.0-164+1ubuntu7.2_i386.deb
vim-tiny_1%3a7.0-164+1ubuntu7.2_i386.deb
xawtv_3.95.dfsg.1-2ubuntu1_i386.deb
xawtv-plugins_3.95.dfsg.1-2ubuntu1_i386.deb


I am assuming I remove everything under "partial"?

I removed all the "postgresql" packages on this list, then ran "sudo apt-get install -f" in terminal (the updater was broken). It gave me a list of packages to autoremove, then suggested I reinstall postgresql 8.1 and its dependencies, as well as postgresql 8.2. I got errors when 8.2 began to install.
but the updater still is trying to install postgresql-8.2. I still get errors when running update, and cannot completely remove using synaptic.

---

