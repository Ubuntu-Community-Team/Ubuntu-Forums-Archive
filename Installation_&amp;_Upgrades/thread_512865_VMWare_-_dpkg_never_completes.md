---
title: "VMWare - dpkg never completes"
date: 2007-07-29
forum: Installation &amp; Upgrades
---

### Post by jeromio on 2007-07-29
I apologize if this is discussed in another thread - found some close ones, but not exactly the same. My issue is that I want to have VMWare Player. I don't want to uninstall it. It is installed and it works. However, the dpkg command doesn't think it's installed - or it thinks something went wrong. SO it is perpetually trying to finish. Whenever I do anything with packages, I have to answer the same stupid vmware questions about virtual ethernet, etc. It always ends the same way - there are 2 failures:

> Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                  failed
   Host-only networking on /dev/vmnet1 (background)                    done
   Host-only networking on /dev/vmnet8 (background)                    done
   NAT service on /dev/vmnet8                                         failed
invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error processing vmware-player (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-player

These are unimportant since vmware works and has networking, etc. But it looks like those failures mark vmware as being not fully installed. SO it always tries again. 

There are other posts that talk about how to kill it - how to delete /etc/vmware and etc in order to make an uninstall stay that way. But I want to keep vmware. I just want it to stop trying to configure itself. Any ideas?

---

