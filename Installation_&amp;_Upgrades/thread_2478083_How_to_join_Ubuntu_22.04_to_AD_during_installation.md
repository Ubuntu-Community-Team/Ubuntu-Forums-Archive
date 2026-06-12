---
title: "How to join Ubuntu 22.04 to AD during installation"
date: 2022-08-16
forum: Installation &amp; Upgrades
---

### Post by talekksna on 2022-08-16
Hi, I have question regarding joining Ubuntu 22.04 to AD during installation. When I define and fill out "Your Name", "Device Name" (with FQDN), "Username" - do I enter here my username in active directory?? and "Password" - do I enter here AD user password??
And at the end of the page I select option to join AD and click next.
On the next page I gat "FQDN of the server AD" and I enter "server.domen.com", the I fill username that have rights to do joining of device to AD and password for that user.
What is next? Is this correct way that I described here?

I read "White paper" but I did not understand what is the process after this steps that I describe.

Can anyone help me?

Thank you.

---

### Post by kevidigi on 2022-08-16
Perhaps you could install and then join to Active Directory afterwards, as described here: [https://computingforgeeks.com/join-ubuntu-debian-to-active-directory-ad-domain/](https://computingforgeeks.com/join-ubuntu-debian-to-active-directory-ad-domain/)

---

### Post by talekksna on 2022-08-17
Thank you. I saw that. Never the less, I am interested if anyone know how to that during installation.

---

### Post by ActionParsnip on 2022-08-17
[https://docs.microsoft.com/en-us/azure/active-directory-domain-services/join-ubuntu-linux-vm](https://docs.microsoft.com/en-us/azure/active-directory-domain-services/join-ubuntu-linux-vm)
Note that this is VERY case sensitive

---

