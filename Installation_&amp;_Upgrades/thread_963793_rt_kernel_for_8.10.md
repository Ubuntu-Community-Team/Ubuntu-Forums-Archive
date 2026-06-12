---
title: "rt kernel for 8.10?"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by kakyoism on 2008-10-30
Hi,

I'm considering whether to upgrade to Intrepid or not, because there seemed to be messages saying no realtime support for Intrepid for now.

But all those messages came from weeks ago, I wonder whether things have changed or not.

Thanks.

---

### Post by Elfy on 2008-10-30
I don't think that they have changed as yet, I'd certainly be inclined to follow the release notes for the moment

> UbuntuStudio real-time kernel support

The real-time kernel variant included in Ubuntu 8.10 does not include SMP support. Users of UbuntuStudio 8.04 who need real-time kernel support for dual-core, dual-processor, or more complex SMP configurations are advised not to upgrade to UbuntuStudio 8.10 at this time. 

---

### Post by logos34 on 2008-10-30
you mean the linux-rt pkg

[http://packages.ubuntu.com/search?keywords=linux-rt&searchon=names&suite=intrepid&section=all](http://packages.ubuntu.com/search?keywords=linux-rt&searchon=names&suite=intrepid&section=all)

doesn't have smp support?

If not, you could always easily compile your own with [KernelCheck. ]("http://kcheck.sourceforge.net/")

---

### Post by Oele on 2008-10-30
Indeed. Just upgraded my 8.04 box with rt kernel to 8.10 and now it only sees one CPU core. :(

---

### Post by stmiller on 2008-11-03
> **Oele said:**
> Indeed. Just upgraded my 8.04 box with rt kernel to 8.10 and now it only sees one CPU core. :(

Same here. Grrr...

---

