---
title: "Asterisk not working after upgrade to 15.04"
date: 2015-05-24
forum: Installation &amp; Upgrades
---

### Post by matthys on 2015-05-24
Again Asterisk gets broken when doing an upgrade, which I should have know before.

Not much info to find. I even did a clean installation of Asterisk and getting these kind of messages;
[May 24 16:38:15] Asterisk 13.1.0~dfsg-1ubuntu2 built by buildd @ allspice on a x86_64 running Linux on 2015-01-06 12:16:35 UTC
[May 24 16:38:16] NOTICE[969] cdr.c: CDR simple logging enabled.
[May 24 16:38:16] ERROR[969] config.c: The file 'manager.d/*.conf' was listed as a #include but it does not exist.
[May 24 16:38:16] NOTICE[969] manager.c: Unable to open AMI configuration manager.conf, or configuration is invalid.
[May 24 16:38:16] NOTICE[969] loader.c: 300 modules will be loaded.
[May 24 16:38:16] WARNING[969] loader.c: Error loading module 'res_pjsip_pidf_digium_body_supplement.so': /usr/lib/asterisk/modules/res_pjsip_pidf_digium_body_supplement.so: undefined symbol: ast_sip_presence_xml_create_node
[May 24 16:38:16] WARNING[969] loader.c: Error loading module 'res_stasis_answer.so': /usr/lib/asterisk/modules/res_stasis_answer.so: undefined symbol: stasis_app_send_command
[May 24 16:38:16] WARNING[969] loader.c: Error loading module 'res_pjsip_session.so': /usr/lib/asterisk/modules/res_pjsip_session.so: undefined symbol: ast_sip_location_retrieve_contact_from_aor_list
[May 24 16:38:16] WARNING[969] loader.c: Error loading module 'res_ari_asterisk.so': /usr/lib/asterisk/modules/res_ari_asterisk.so: undefined symbol: stasis_app_ref
[May 24 16:38:16] WARNING[969] loader.c: Error loading module 'res_pjsip_authenticator_digest.so': /usr/lib/asterisk/modules/res_pjsip_authenticator_digest.so: undefined symbol: ast_sip_unregister_authenticator
[May 24 16:38:16] WARNING[969] loader.c: Error loading module 'res_fax_spandsp.so': /usr/lib/asterisk/modules/res_fax_spandsp.so: undefined symbol: ast_fax_state_to_str
[May 24 16:38:16] WARNING[969] loader.c: Error loading module 'res_hep_rtcp.so': /usr/lib/asterisk/modules/res_hep_rtcp.so: undefined symbol: hepv3_create_capture_info
...
[May 24 16:38:20] WARNING[969] loader.c: Error loading module 'res_ari_playbacks.so': /usr/lib/asterisk/modules/res_ari_playbacks.so: undefined symbol: stasis_app_playback_to_json
[May 24 16:38:20] WARNING[969] loader.c: Module 'res_ari_playbacks.so' could not be loaded.
[May 24 16:38:20] WARNING[969] loader.c: Error loading module 'res_ari_channels.so': /usr/lib/asterisk/modules/res_ari_channels.so: undefined symbol: stasis_app_playback_to_json
[May 24 16:38:20] WARNING[969] loader.c: Module 'res_ari_channels.so' could not be loaded.

I was running Asterisk 11.11.0~dfsg-2ubuntu1 before but it seems you cannot downgrade to this version on Ubuntu 15.04 :-(

Any advise how to fix this?

Seems a bit similar to this bug-report -> [https://bugs.launchpad.net/ubuntu/+source/asterisk/+bug/1458323](https://bugs.launchpad.net/ubuntu/+source/asterisk/+bug/1458323)
But I would think there is something wrong with the modules ....

PS .. if there is somebody who knows how to perform downgrade to Asterisk 11.11 on Ubuntu 15.04, please tell me.

Thanks,
Matthijs

---

### Post by dino99 on 2015-05-24
the error is : ******* ERROR[969] config.c: The file 'manager.d/*.conf' was listed as a #include but it does not exist. *************

so maybe you can dig around 'config.c' and [PHP]sudo journalctl[/PHP] should warns about errors

---

### Post by matthys on 2015-05-24
No journal files were found.

The manager.d/*.conf is not really a problem ... still had a copy of the old config and copied the empty readme.conf in manager.d.
The real problem are all these .so files which are not loaded ....

---

### Post by mc4man on 2015-05-24
All the releases for 15.04 during it's dev are listed here (- Releases in Ubuntu
[https://launchpad.net/ubuntu/vivid/+source/asterisk](https://launchpad.net/ubuntu/vivid/+source/asterisk)

You could pick one, on the resulting page you'll see a "Builds" section on middle right. From there the Arch links will give a page with actual packages (scroll down to > Binary Packages
You'd need to first determine all asterisk source packages you currently have installed, then download all of the currently installed ones  from the proper arch page into an empty folder you create.

When done cd to that folder & go 
```
sudo dpkg -i *.deb
```
If dpkg shows an error then read & correct if possible. If older version isn't usable then upgrade back to current or just plain remove/not use until bug is addressed.

Probably best to have synaptic available to see what's installed & in worst case, broken packages that you can't resolve,  then easy to fix or remove...

---

### Post by matthys on 2015-05-24
Tried to manually install all Asterisk 11.11 deb files but failed due dependencies :-(

---

### Post by mc4man on 2015-05-24
> **matthys said:**
> Tried to manually install all Asterisk 11.11 deb files but failed due dependencies :-(

I can't say what that means without the complete terminal output .
 If I take "all Asterisk 11.11 deb files" literally then that is not what I told you to try. Only ones that are currently installed in your system, not  'all of them'

---

### Post by matthys on 2015-05-26
Just to let you know .. I will no longer bother using Asterisk on Ubuntu ... it just get broken to many times :-(

---

