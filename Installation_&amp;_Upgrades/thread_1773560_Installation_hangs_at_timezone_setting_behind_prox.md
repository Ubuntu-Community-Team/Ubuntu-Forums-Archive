---
title: "Installation hangs at timezone setting behind proxy"
date: 2011-06-02
forum: Installation &amp; Upgrades
---

### Post by shnplr on 2011-06-02
Hi,

Does anyone know what type of request (e.g. url, protocol, port etc) is run to retrieve the timezone at the early stages of install?

I'm installing behind an unauthenticated proxy at work.  I've set the proxy at:

1. Network Settings
2. terminal using export http_proxy=http://myproxy.etc:80/
3. performed an apt-get update successfully
4. Entered into Symantic for good luck
5. Entered it into FF and can browse internet successfully.

However when I install it just hangs at the timezone/region screen displaying "New York".

After about 10-15 minutes the install continued very slowly....it displayed some message about changing over to text (something or other) - eventually I noticed it was downloading linux-kernal (which seems weird as shouldn't that be on the DVD?).  After about 2 hours I finall got the desktop, when I rebooted grub2 loads successfully however it boots into some initramfs console prompt (somethng like that) - so obviously somethings not right.

My home installation only took about 15 minutes - so I'm assuming our work proxy must be blocking something that the install needs.

I thought if I could find out the service/server used to gather tmiezone information I could test this before starting the install to confirm whether its proxy problem or not.

Any other advice/suggestion appreciated

Cheers,
Paul

---

