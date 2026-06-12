---
title: "[rant] did policykit change my settings?"
date: 2008-10-13
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by wizard10000 on 2008-10-13
Well, a small rant anyway  :)

Ran update-manager on my Hardy box and spent an hour afterward trying to figure out why a normal user couldn't mount a USB hard drive.

I can't look back at the old installation to tell, but either that particular privilege wasn't in Hardy or policykit changed it because that function worked just fine in Hardy.  Not sure which is the case so I don't wanna bug it but I can see about fifty billion people calling the helpdesk because they can no longer mount a removable drive.

Can someone clarify?  Did policykit change an existing policy on upgrade or is this a new policy?  If this is a new policy can we have a mechanism in place that informs the user they don't have rights to mount a removable drive?

---

### Post by cariboo on 2008-10-13
Have  you got Access External Storage Devices Autiomatically checked in System-->Administration-->Users and Groups--><user>-->Properties-->User Privileges?

Jim

---

### Post by wizard10000 on 2008-10-14
> **cariboo907 said:**
> Have  you got Access External Storage Devices Autiomatically checked in System-->Administration-->Users and Groups--><user>-->Properties-->User Privileges?

Jim

I just checked, and - yup.  Authorizing removable storage devices in System --> Administration --> Authorizations is what fixed the problem.

IM frequently less than HO it's a bad idea to change security settings during an upgrade.  I might expect it on a clean install, but not during an upgrade.

---

