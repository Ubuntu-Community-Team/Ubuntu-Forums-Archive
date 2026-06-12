---
title: "Roming Profiles on Ubuntu Server"
date: 2012-10-09
forum: Installation &amp; Upgrades
---

### Post by BrijeshTrivedi on 2012-10-09
Hi all,

I want to set up Roaming Profiles on Ubuntu Server, so users can login into any computer.[B] 

Scenario [/B]

I want user to store all there files on the server and they can able to log in from any PC and access there data. 

Please provide with this solution 

Thanking you :popcorn:

---

### Post by dcstar on 2012-10-10
> **BrijeshTrivedi said:**
> 
........
Please provide with this solution 


Or you could find the solution yourself instead of expecting others to serve it up to you, eh?

---

### Post by Lars Noodén on 2012-10-10
There are at least a couple of ways to do it.  

One way might be to manage users with Kerberos, groups with OpenLDAP and home directories with NFS or OpenAFS.

Another might be to use LTSP.  Roaming profiles are part and parcel of LTSP.

---

