---
title: "Need Help Installing OpenVPN......"
date: 2006-10-17
forum: Installation &amp; Upgrades
---

### Post by necron_09 on 2006-10-17
im new to linux and im using ubuntu 5.10 and trying to install OpenVPN for project purposes.
so far ive done the ./configure and proceeded to compile the sources. the errors shown below are what i got
when i tried to 'make install'. Any idea how i can solve this problem? ty


flame@ubuntu:~/Desktop/openvpn-2.0.9$ make
make  all-am
make[1]: Entering directory `/home/flame/Desktop/openvpn-2.0.9'
make[1]: Leaving directory `/home/flame/Desktop/openvpn-2.0.9'
flame@ubuntu:~/Desktop/openvpn-2.0.9$ make install
make[1]: Entering directory `/home/flame/Desktop/openvpn-2.0.9'
test -z "/usr/local/sbin" || mkdir -p -- . "/usr/local/sbin"
  /usr/bin/install -c 'openvpn' '/usr/local/sbin/openvpn'
/usr/bin/install: cannot remove `/usr/local/sbin/openvpn': Permission denied
make[1]: *** [install-sbinPROGRAMS] Error 1
make[1]: Leaving directory `/home/flame/Desktop/openvpn-2.0.9'
make: *** [install-am] Error 2
flame@ubuntu:~/Desktop/openvpn-2.0.9$

---

