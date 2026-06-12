---
title: "Ettercap libpcap 0.8.1"
date: 2011-09-30
forum: Installation &amp; Upgrades
---

### Post by FOn1NbX244 on 2011-09-30
Hey guys,
  I am trying to install ettercap from its source files.But during ./configure fails because of libpcap.

configure:error:libpcap >= 0.8.1 required.

I have only libpcap0.8 and I cannot find any libpcap package for ubuntu.
Any workaround or suggestions guys?
Please help..
Thanks in advance....

---

### Post by Dangertux on 2011-09-30
You can download libpcap-1.0.0 source here : [http://archive.ubuntu.com/ubuntu/pool/main/libp/libpcap/libpcap_1.0.0.orig.tar.gz](http://archive.ubuntu.com/ubuntu/pool/main/libp/libpcap/libpcap_1.0.0.orig.tar.gz)

Just compile it should satisfy the ettercap dependency.

---

### Post by FOn1NbX244 on 2011-09-30
> **Dangertux said:**
> You can download libpcap-1.0.0 source here : [http://archive.ubuntu.com/ubuntu/pool/main/libp/libpcap/libpcap_1.0.0.orig.tar.gz](http://archive.ubuntu.com/ubuntu/pool/main/libp/libpcap/libpcap_1.0.0.orig.tar.gz)

Just compile it should satisfy the ettercap dependency.

Hey thanks for a quick reply,
hmm,no it doesn't work.I think it needs libpcap0.8.1.Not libpcap-1.1.1.Because they are different contexts.I already have the 1.1.1 version in your context.But it still doesnt work.Same error.

---

### Post by Dangertux on 2011-09-30
> **indianaronaldo said:**
> Hey guys,
  I am trying to install ettercap from its source files.But during ./configure fails because of libpcap.

configure:error:libpcap >= 0.8.1 required.

I have only libpcap0.8 and I cannot find any libpcap package for ubuntu.
Any workaround or suggestions guys?
Please help..
Thanks in advance....

Hmm I'm pretty sure it should work on 1.0.0 or 1.1.1 but here is the link for 0.8.1 try that.

[http://packetstormsecurity.org/files/view/32611/libpcap-0.8.1.tar.gz](http://packetstormsecurity.org/files/view/32611/libpcap-0.8.1.tar.gz)

and 0.9.8

[http://pkgs.fedoraproject.org/repo/pkgs/libpcap/libpcap-0.9.8.tar.gz/5208f24d0328ee7c20b52c43eaa9aa0e/](http://pkgs.fedoraproject.org/repo/pkgs/libpcap/libpcap-0.9.8.tar.gz/5208f24d0328ee7c20b52c43eaa9aa0e/)


Hope that helps.

---

### Post by FOn1NbX244 on 2011-10-01
> **Dangertux said:**
> Hmm I'm pretty sure it should work on 1.0.0 or 1.1.1 but here is the link for 0.8.1 try that.

[http://packetstormsecurity.org/files/view/32611/libpcap-0.8.1.tar.gz](http://packetstormsecurity.org/files/view/32611/libpcap-0.8.1.tar.gz)

and 0.9.8

[http://pkgs.fedoraproject.org/repo/pkgs/libpcap/libpcap-0.9.8.tar.gz/5208f24d0328ee7c20b52c43eaa9aa0e/](http://pkgs.fedoraproject.org/repo/pkgs/libpcap/libpcap-0.9.8.tar.gz/5208f24d0328ee7c20b52c43eaa9aa0e/)


Hope that helps.


Ok,I'll check this out now.But the thing is even after I installed the 1.0.0 you gave me yesterday,the synaotic manager still shows the 0.8 version.Anyways,First lemme try these two you gave now.

---

### Post by buckbugs on 2011-10-06
i got this error during compiling all libpcap version :(

checking for capable lex... insufficient
configure: error: Your operating system's lex is insufficient to compile
 libpcap.  flex is a lex replacement that has many advantages, including
 being able to compile libpcap.  For more information, see
 [http://www.gnu.org/software/flex/flex.html](http://www.gnu.org/software/flex/flex.html) .


im using ubuntu maverick 64bit anyway

---

### Post by Dangertux on 2011-10-06
> **buckbugs said:**
> i got this error during compiling all libpcap version :(

checking for capable lex... insufficient
configure: error: Your operating system's lex is insufficient to compile
 libpcap.  flex is a lex replacement that has many advantages, including
 being able to compile libpcap.  For more information, see
 [http://www.gnu.org/software/flex/flex.html](http://www.gnu.org/software/flex/flex.html) .


im using ubuntu maverick 64bit anyway

This should install flex you may also want to install bison

```

sudo apt-get install flex

```

```

sudo apt-get install bison

```

Hope that helps, in the future you should start your own thread, it makes it more likely you will get the support you're looking for.

Thanks :-)

---

