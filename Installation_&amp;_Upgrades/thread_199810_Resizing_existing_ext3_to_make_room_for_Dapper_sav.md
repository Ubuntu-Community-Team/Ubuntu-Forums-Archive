---
title: "Resizing existing ext3 to make room for Dapper save?"
date: 2006-06-19
forum: Installation &amp; Upgrades
---

### Post by teevee on 2006-06-19
Hi all,

been using Ubuntu since the very first version, always upgrading from one version to another, but want to do a "clean install" of Dapper next to my existing Breezy now. Is it save resizing the Breezy ext3 partition using the Dapper install CD? I still want to be able booting into Breezy afterwards.

---

### Post by cacharreo on 2006-06-19
You can try the ***qtparted***d package:
[http://qtparted.sourceforge.net](http://qtparted.sourceforge.net).
But please, backup first!!!!!! 8-[

---

### Post by az on 2006-06-19
[QUOTE=teevee]Is it safe resizing the Breezy ext3 partition using the Dapper install CD? I still want to be able booting into Breezy afterwards.[/QUOTE]

Yes.  That is the safest and easiest way to go.  Just boot from the cd and it will default to offering to shrink your partition down for you.

---

