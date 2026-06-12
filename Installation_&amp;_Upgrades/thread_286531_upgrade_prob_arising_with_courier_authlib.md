---
title: "upgrade prob arising with courier authlib"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by Calculator on 2006-10-27
On running "update-manager -c" to upgrade to eftyedge from Dapper Drake I get the following problem with courier-authlib and the update fails midway.

On rebooting and running Synaptic I get "You have 3 broken packages on your system!" whaich are listed as:

1) Courier-authdaemon; 
2) courier-authlib;and 
3) associated package.

When I mark these for reinstallation I get "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem."

On performing this task results in -

... subprocess post-installation script returned error exit status 3
dpkg: dependency problems prevent configuration of courier-authlib-userdb:
 courier-authlib-userdb depends on courier-authlib; however:
  Package courier-authlib is not installed.
 courier-authlib-userdb depends on courier-authlib (>= 0.58); however:
  Package courier-authlib is not installed.
dpkg: error processing courier-authlib-userdb (--configure):
 dependency problems - leaving unconfigured ...

Trying to reinstall courier-authlib alone reults in an error.

What can I do?

Thanks

---

### Post by Calculator on 2006-10-28
Problem answered - see thread: [http://www.ubuntuforums.org/showthread.php?t=285466&highlight=courier](http://www.ubuntuforums.org/showthread.php?t=285466&highlight=courier)

Thanks

---

