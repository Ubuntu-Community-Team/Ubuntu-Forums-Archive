---
title: "Is a PXE server right for this?"
date: 2017-02-23
forum: Installation &amp; Upgrades
---

### Post by MetalMusicAddict on 2017-02-23
I currently flash Windows to new machines at my work with a USB thumb drive running Ubuntu. The drive runs live with a persistent partition that contains a .IMG file that gets DD'd to the actual hard drive of the target machine. All works off a little script I put together. I can even set things up to pull an alternative .IMG from across the network.

Which got me thinking...

Can I set up a PXE server to boot my custom Ubuntu+script over the network to the client PC? Eliminating the thumb drive altogether? For that matter, can a PXE server use a .IMG and just write it directly to the client hard drive?

If I can just set the client machine to network boot and everything just runs from there that would be fantastic.

---

### Post by TheFu on 2017-02-23
Almost anything you can dream is possible, with a little coding. 

It is definitely possible to network boot systems.

It is definitely possible to netwokr boot AND then install systems, unattended.

However ... depending on the number of systems, something like **cobbler** might be a better solution. [https://cobbler.github.io/manuals/quickstart/](https://cobbler.github.io/manuals/quickstart/) Just be really careful, since people have reloaded every client system on a subnet by accident with tools like this. [https://www.reddit.com/r/sysadmin/comments/260uxf/emory_university_server_sent_reformat_request_to/](https://www.reddit.com/r/sysadmin/comments/260uxf/emory_university_server_sent_reformat_request_to/)

Definitely setup a lab to test inside first.

---

