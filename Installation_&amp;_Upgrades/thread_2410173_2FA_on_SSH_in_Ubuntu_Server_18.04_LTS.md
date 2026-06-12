---
title: "2FA on SSH in Ubuntu Server 18.04 LTS"
date: 2019-01-11
forum: Installation &amp; Upgrades
---

### Post by smunir on 2019-01-11
I want to set up 2FA on SSH on my Ubuntu 18.04 LTS Server. I don't want to use Google Authenticator but Open Source solution.


  Are there any guides for just using something free and other than Google Authenticator?

  
Thank you in advance.

  
Regards,

---

### Post by TheFu on 2019-01-12
Like [https://developers.yubico.com/pam-u2f/](https://developers.yubico.com/pam-u2f/) ?

Before you decide on a solution, consider all the different clients which might need ssh access and whether u2f will work from that client. For example, if you connect from a tablet or phone, how will the 2nd HW device validate if it only has USB interface?

Also, might want to have local access never use U2F, assuming physical security is sufficient for the machine.

I setup u2f with my nextcloud server and it was great from desktop clients - beautiful.  But none of my tablets or phones could access it.  I have 2 different Yubikey devices - a Neo and a cheap U2F-only device.  The Neo supports 4 different authentication methods including u2f and NFC.  I'd hoped that NFC would be useful, but it only worked about 10% of the time.  since those tests, I've gotten a new phone and new tablets - none of NFC support.   With Nextcloud, there is a way to print out 20 character login codes for use from non-U2F devices.  These are 2nd factor, so after the normal password has been entered already.  In theory, setting up ssh with something like this is possible.

But if you are using ssh with ssh-keys for authentication, and unlocking the keys requires authentication already, isn't that 2FA already?
* you must have the ssh-key
* you must unlock it before use on the client-side
* you must have already setup/sent the public-ssh-key to the server

Blocking passwords for ssh/scp/sftp/rsync/sshfs and the 50 other ssh-based remote connection tools from internet connections is basic ssh security already.  If you run something like fain2ban or deny hosts, then brute-force attacks are effectively handled.

Anyways, interesting problem.  Google did find a few people who implemented 2FA for ssh on Debian/Ubuntu systems. None on 18.04 that I saw, however.

---

