---
title: "Server Certificate Verification Failed"
date: 2017-05-10
forum: Installation &amp; Upgrades
---

### Post by eligible on 2017-05-10
[FONT=Helvetica]Hi There
I'm using GITLab since the version 8.10.2, I've just upgraded to the latest version 9.1.3 and after that I'm not able to clone my projects, following error occur:

[/FONT][FONT=Helvetica]server certificate verification failed. CAfile: /etc/ssl/certs/ca-certificates.crt CRLfile: none

[/FONT][FONT=Helvetica]I've done the following steps but no luck ...
apt-get install --reinstall ca-certificates
update-ca-certificates

[/FONT][FONT=Helvetica]My OS is Ubuntu 14.04.5 LTS and the Web version with HTTPS is running fine, I've googled a lot but not find a correct way to resolve this issue.[/FONT]
[FONT=Helvetica]
Thanx in Advance[/FONT]

---

### Post by eligible on 2017-05-11
git config --global http.sslverify false


Worked for me, but is it safe?

---

### Post by brad_richards on 2017-05-15
Possibly related? I came here today to ask for help with a browser certificate problem. I have a PC and a laptop with (theoretically) identical Ubuntu 16.04 installations. Starting about a week ago, Firefox and Cisco applications on the PC claim that certain sites have invalid certificates (specific error: "Certificate is from an untrusted source"). Chromium is happy with the certificates. Firefox and Cisco on the laptop also report no problems. I am at a loss to explain why only certain application on one of two "identical" installations would report invalid certificates.

Anyone have any hints as to where to look for the problem?

---

### Post by brad_richards on 2017-05-15
Found the problem, although I don't understand the cause. Apparently Cisco also relies on Firefox for certificates. In Firefox, the certificate database was damaged (certutil could not open it). Deleting the profile and creating a new one solved the problem, both for Firefox and for Cisco AnyConnect. So this is unlikely to be relevant to the original poster's problem with GitLab.

---

