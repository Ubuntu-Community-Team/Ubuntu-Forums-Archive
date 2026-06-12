---
title: "Grub error when installing distro without cd"
date: 2010-05-10
forum: Installation &amp; Upgrades
---

### Post by pumrel on 2010-05-10
Hi, I'm really helpless here :(
I've just wanted to try another distro and install it on another harddrive and I read somewhere that it's possible to install it from harddrive withou using a cd. I thought that it would be really nice as I would spare a lot of disks:)

I was trying to install OpenSuse, so I copied linux and initrd from /boot/x86_64/loader/ on the cd to the /boot dir.
Then I added this to the /etc/grub.d/40_custom
```
echo "Install Entry" >&2
cat << EOF
menuentry "OpenSuse 11.2 install" {
        set root='(hd2,1)'
        linux	/boot/linux root=UUID=2dd22c6c-363d-4939-bd52-c04309026581 ro
        initrd	/boot/initrd
}
EOF

```
However I always get error: file not found in grub.
I believe it should be allright, because the other info is taken from my K/Ubuntu entry in grub.cfg

Is there somebody more experienced than me in this? I can't seem to fix it. :(

---

