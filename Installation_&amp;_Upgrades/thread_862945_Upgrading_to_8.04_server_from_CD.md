---
title: "Upgrading to 8.04 server from CD"
date: 2008-07-18
forum: Installation &amp; Upgrades
---

### Post by rxbandit on 2008-07-18
So I'm trying to upgrade my server/mythbackend, has XFCE for a WM. So I've mounted the iso up that i downloaded at work.
By using the following command: 
mount -o loop -t iso9660 /mnt/upload/ubuntu-8.04.1-server-amd64.iso /media/cdrom0/

then i issue the following:
root@mythfileserver:/media/cdrom0# gksu "sh /media/cdrom0/cdromupgrade"

(gksu:7310): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.

(hardy:7317): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
Warning update-manager unsupported locale setting
gpgv: Signature made Mon Jun 30 21:38:26 2008 PDT using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
Segmentation fault (core dumped)


Anyone have any suggestions, I'm abit stumped. Possibly missing some GTK stuff? Is there another way to install from the cd without lanuching the GUI update manager.

---

### Post by rxbandit on 2008-07-18
So i figured it out.....I added my CDROM as a source in my /etc/apt/sources.list and commented out all my internet sources. Then did a; apt-get dist-upgrade. All is well, upgraded cleanly.:guitar:

---

