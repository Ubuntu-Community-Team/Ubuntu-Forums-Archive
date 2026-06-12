---
title: "Smbfs mouintpoints have to be remounted after resuming??"
date: 2005-05-31
forum: Installation &amp; Upgrades
---

### Post by coaxx on 2005-05-31
Hello to this great and helpfull community!!

My Problem:

I successfully set up to mount smb shares during bootup with this guide: [http://www.ubuntuguide.org/#automountnetworkfolders](http://www.ubuntuguide.org/#automountnetworkfolders)

Things work really well till I come back from resuming (here I use Suspend to Ram *yiepehhh* :-)) As soon as my notebook is back from standby I cannot access the smbfs mounpoints anymore (ls /mnt/smbmount will result in a 30sec delay and then I get an input/output error) A simple remount will solve the problem and the shares are again fully accessible.

Here are no error messages while resuming an network-connections work well! Any suggestions? How to auto remount after resuming? (at least it wouldt be a workaround)

Thanks!

---

### Post by coaxx on 2005-05-31
ooops i posted under Warty Forum :(

**Couldt a mod please move this thread to the Hoary installation forum? thank you!**

---

