---
title: "Issue Following Upgrade Related to Upgrade?"
date: 2013-09-09
forum: Installation &amp; Upgrades
---

### Post by wblogan2 on 2013-09-09
I'm not sure if this is an upgrade or LAMP or some other coincidental problem, but the problem did not manifest until after a version upgrade, and I have been unable to find anything helpful on the web, including the Ubuntu forums. So I am asking here for some insight as to what the problem might be, or where to go to find help.

Yesterday I upgraded from 12.04 to 12.10 to 13.04 via the update manager. Expecting that some minor adjustments would be necessary, all went well so far as I know. However, there is one thing that I can not explain or diagnose.

I had LAMP (Linux Apache MySQL PHP) server installed and working properly under 12.04 and 12.10. After the upgrade to 13.04, I can access the localhost as I could under 12.04 and 12.10. But when I attempt to access the external domain of one of the sites of which I have a mirror on the localhost, it resolves to the localhost and not to the external domain. I.e., [http://www.domain.com](http://www.domain.com) resolves to [http://localhost/domain](http://localhost/domain). Another mirror I maintain on the localhost resolves correctly (i.e., [http://local/domain](http://local/domain) resolves to [http://local/domain](http://local/domain), and [http://domain.com](http://domain.com) resovles to [http://domain.com](http://domain.com)). Furthermore, I have asked a neighbor to attempt to access the domain with which I am having difficulty, and it returns an error message ("unable to establish connection").

TIA. 
--
Regards,
Bill

---

### Post by wblogan2 on 2013-09-10
Turns out the problem had nothing to do with Ubuntu 13.04, or my installation of it, but with the regristrar and/or host of the domain(s) I referenced. If I can figure out how to mark this solved or delete it, I'll do so.

---

