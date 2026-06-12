---
title: "Improving boottime: &quot;configuring network interfaces&quot;"
date: 2005-04-19
forum: Installation &amp; Upgrades
---

### Post by RAF on 2005-04-19
Hi,

I know there has been a similar thread before in this forum, but the question there was not answered...

Everytime I boot my Ubuntu it spends a lot of time in "configuring network interfaces" (I think it is because of dhcp) and I'd like to change that. In the mentioned thread, Strg+C was an idea, but I don't think that this is a appropriate solution. Can't this step in the boot progress be made quicker? Maybe it could be done in background? How?

I think that's quite an easy question, but I'm a Newbie in Linux...

Could anyone help me, please?

---

### Post by bored2k on 2005-04-19
Go to /etc/init.d/ and chmod -x the file or "step" you don't want ubuntu to run @ startup.

---

