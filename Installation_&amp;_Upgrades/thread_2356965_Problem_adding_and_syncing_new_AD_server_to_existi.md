---
title: "Problem adding and syncing new AD server to existing AD"
date: 2017-03-28
forum: Installation &amp; Upgrades
---

### Post by mickier2 on 2017-03-28
I inherited an AD "domain" which is running Ubuntu 14.04, with Samba 4.1.6 with "built-in" AD-DNS.  The network has only one AD server, which runs on KVM as a guest - (convenient so I can make backups and test stuff without breaking my network - and my users are still unaffected.

We have around 500 users on the system, and I'm trying to upgrade to 16.04 and a more current version of Samba without making all my users create new passwords...  

The problem I have run into is that when I try and upgrade Ubuntu to the latest version of 14.04 (required to get to 16.04), samba breaks badly.  I have chased the errors for hours, searching forums, and haven't gotten anywhere - Once I did finally get to the point that samba would actually *start* but my shares wouldn't mount - "bad credentials"... - and I was concerned about carrying along issues from this AD server which might plague me in the future! SO - I thought - "HEY - let me just add a 2k8 server as an AD server, and sync everything - then I can start over with a new samba server, join the AD and voila!... 

When I attempt to join the 2k8 server to the AD as an AD server, it joins just fine - EXCEPT it will not join/synchronize the DNS.  It gives an error - A delegation for this DNS server cannot be created because the authoritative parent zone cannot be found or it does not run Windows DNS server. If you are integrating with an existing DNS infrastructure you should manually create a delegation to this DNS server in the parent zone...", When I go into AD DNS manager, there's an error which says "DNS server was unable to initialize Active Directory security interfaces. Check that AD is functioning properly..." 

I guess the problem is that I just don't know how to create a delegation in the authoritative parent zone on the samba server - and from the searching I've done - it seems that I shouldn't have to do that - [https://wiki.samba.org/index.php/Joining_a_Windows_Server_2008_/_2008_R2_DC_to_a_Samba_AD](https://wiki.samba.org/index.php/Joining_a_Windows_Server_2008_/_2008_R2_DC_to_a_Samba_AD)  seems to indicate that once you join a 2k8 (or 2012) server, the DNS should auto-replicate...
 
Next I tried running RecoveryManager Plus from ManageEngine - to make a full AD backup - hoping to restore to a fresh AD server - it backs up all the AD users/groups/containers, but when it hits the DNS, it crashes - and SAMBA does a KERNEL PANIC. INTERNAL ERROR: Signal 11 /lib/util/fault.c:75*fault_report) and (smb_panic_default)

Of course when I temporarily shut down the samba server (which is the *only* existing DNS), the w2k8 server won't even start AD - and I'm dead.  

Next, I tried to create a new zone in 2k8 DNS, but it won't let me use the existing domain... 

I also followed the directions to migrate from samba_AD_DNS to BIND9, and that operation *says* it completed successfully - but samba won't run... 
followed this link: [https://wiki.samba.org/index.php/Changing_the_DNS_Back_End_of_a_Samba_AD_DC](https://wiki.samba.org/index.php/Changing_the_DNS_Back_End_of_a_Samba_AD_DC)

Bottom line - All I want is a reasonably current version of AD on Samba (or even Windows) which contains my users and their log in credentials... -- which is, HOPEFULLY  free of any - left-over debris from the current AD forest - so that I don't run into further issues/problems next time I need to upgrade(!) 

So far, I have not figured out a way to get from where I am - to a fresh samba or 2k8 or 2012 server.  But as I said - I am not *DOWN* - so life is still good!

---

