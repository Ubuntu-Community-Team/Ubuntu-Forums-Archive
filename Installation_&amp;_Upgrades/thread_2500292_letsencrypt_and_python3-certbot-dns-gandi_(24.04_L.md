---
title: "letsencrypt and python3-certbot-dns-gandi (24.04 LTS)"
date: 2024-08-29
forum: Installation &amp; Upgrades
---

### Post by matthys on 2024-08-29
Hello, I recently moved from 22.04 LTS to 24.04 LTS and encounter a problem with letsencrypt.

I now get:
Failed to renew certificate <domain> with error: **The requested certbot-plugin-gandi:dns plugin does not appear to be installed**

I checked, and installed and I get: python3-certbot-dns-gandi is already the newest version (1.4.3-2)

What has changed? And how to fix?

---

### Post by currentshaft on 2024-08-29
Is it listed when you run "certbot plugins"?

---

### Post by matthys on 2024-08-30
Okay, I also posted on the letsencrypt forum and this was the problem:

Digging around I just tried to certificate a new sub-domain and test if it works.
Seems some details are changed:
 
In the gandi.ini I changed: certbot_plugin_gandi:dns_api_key => **dns_gandi_api_key**

And this is the new domain config for renewal:
[renewalparams]
account = 
authenticator = **dns-gandi**
dns_gandi_credentials = /etc/letsencrypt/gandi.ini
server = [https://acme-v02.api.letsencrypt.org/directory](https://acme-v02.api.letsencrypt.org/directory)
renew_hook = systemctl reload exim4
**key_type = rsa**

 Though in the test the key_type was ecdsa but now seems to be changed into rsa.

In the forum it was mentioned that "Nowadays Certbot does not use the plugin_name:variable like construction any more".
So I guess this was because of a newer letsencrypt version which came with 24.04 LTS.

Thanks,
Matthijs

(corrected some typos)

---

