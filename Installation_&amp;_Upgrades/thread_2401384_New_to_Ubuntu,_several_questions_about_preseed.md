---
title: "New to Ubuntu, several questions about preseed"
date: 2018-09-17
forum: Installation &amp; Upgrades
---

### Post by gordonmessmer2 on 2018-09-17
I'm struggling to get automated installation working with preseed on 18.04.  I've done automatic installation on earlier releases, but no longer have notes, so I may be missing some things.

The desktop ISO doesn't seem to support preseed.  Is it expected that only the Server ISO does?

I'm unable to use https:// in the URL.  Is that expected?  If so, is providing a checksum the only risk mitigation against content injection and modification attacks?

I'm unable to use a URL that includes a hostname.  A URL that includes an IP address works, but any URL with a hostname causes an error, "wget: bad address 'the.host.name'".  Since I can use an IP address, that suggests that the network is coming up, but the system isn't configuring the resolver.  Is that a bug?

Walking through a manual installation using the server URL, I do see the option to install on LVM, but I don't see any option to encrypt it.  I mean to use "d-i partman-auto/method string crypto" in the preseed file.  Does the server ISO support encrypted installations, or not?

---

