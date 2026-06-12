---
title: "How can you verify download if you cant verify how to verify your download?"
date: 2016-09-19
forum: Installation &amp; Upgrades
---

### Post by pixelfairy2 on 2016-09-19
[http://releases.ubuntu.com/16.04/](http://releases.ubuntu.com/16.04/) and [http://www.ubuntu.com/download/how-to-verify](http://www.ubuntu.com/download/how-to-verify) are both only plain text. tried https on both and it refused connection.

 so you dont even have ssl for the download let alone any of the information your supposed to use to verify the download. someone controlling your router could compromise every step.

searching this before posting, the only hash on an ssl site was here [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD) is that the only reliable download?

---

### Post by TheFu on 2016-09-19
Use the sha1 or sha256 checksums from your mirror download site.  These are gpg signed, so you can validate that as well.
or
Use the built-in validate media option on the boot screen.
or 
Pay for a shipped DVD from a commercial Linux provider for $900.

Your choice.

For me, the sha256 checksums are sufficient with the gpg signatures. You'll have to decide if that is good enough or not.

IMHO, HTTPS doesn't add anything more - just a false sense of security. HTTPS doesn't guaranty security.

---

### Post by pixelfairy2 on 2016-09-19
Im aware of the flaws in https, but it does reduce the number of parties that can mess things up. without it, anyone in control of any router on the way, can put whatever they want in.  its going backwards. all the hashes and key fingerprints are from the same server, making it even easier for whoevers in the middle.

---

### Post by TheFu on 2016-09-20
> **pixelfairy2 said:**
> Im aware of the flaws in https, but it does reduce the number of parties that can mess things up. without it, anyone in control of any router on the way, can put whatever they want in.  its going backwards. all the hashes and key fingerprints are from the same server, making it even easier for whoevers in the middle.

True, using https would make it a tiny-bit harder if they let you go to the correct location at all.

To feed our paranoia:
[http://www.theregister.co.uk/2016/05/27/blue_coat_ca_certs/](http://www.theregister.co.uk/2016/05/27/blue_coat_ca_certs/)
[http://www.nytimes.com/2011/09/06/technology/hacking-in-the-netherlands-broadens-in-scope.html?_r=0](http://www.nytimes.com/2011/09/06/technology/hacking-in-the-netherlands-broadens-in-scope.html?_r=0)
[http://www.theregister.co.uk/2012/02/09/tustwave_disavows_mitm_digital_cert/](http://www.theregister.co.uk/2012/02/09/tustwave_disavows_mitm_digital_cert/)
[http://www.pcworld.com/article/2912752/https-snooping-flaw-in-thirdparty-library-affected-1000-ios-apps-with-millions-of-users.html](http://www.pcworld.com/article/2912752/https-snooping-flaw-in-thirdparty-library-affected-1000-ios-apps-with-millions-of-users.html)

OTOH, we can use different mirrors, check that the sha-checksums and gpg signatures are accurate from different locations. Having HTTPS wouldn't matter.

---

