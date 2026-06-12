---
title: "LTSP Dansguardian Squid on 10.04"
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by dacky on 2010-05-04
I just install Ubuntu 10.04 LTSP.  I am trying to get Dansguardian and Squid to work.  I want to be able to attach Windows machines to the Ubuntu server and connect to the internet, with the Ubuntu server filtering content.  Plus, I want LTSP to work for thin clients.  I had this working with 8.04.

Does anyone have a similar setup working?  What iptable rules do you use?  Anything specific to setup with squid?  The forums I have searched on the web do not work.  I may just go back to my old install.  Something has changed from 8.04 to 10.04.

---

### Post by jackdale on 2010-05-07
:redface: OOPS! I just re-read your quote, I thought you wanted to just configure a simple setup.  Sorry!  (I can't find the delete reply button, - which probabpy means there isn't one!) :redface:

> **dacky said:**
> I just install Ubuntu 10.04 LTSP.  I am trying to get Dansguardian and Squid to work.  I want to be able to attach Windows machines to the Ubuntu server and connect to the internet, with the Ubuntu server filtering content.  Plus, I want LTSP to work for thin clients.  I had this working with 8.04.

Does anyone have a similar setup working?  What iptable rules do you use?  Anything specific to setup with squid?  The forums I have searched on the web do not work.  I may just go back to my old install.  Something has changed from 8.04 to 10.04.

Have you seen this?
[http://www.liberiangeek.net/2010/03/how-to-filter-web-contents-with-danguardian-in-ubuntu/](http://www.liberiangeek.net/2010/03/how-to-filter-web-contents-with-danguardian-in-ubuntu/)
It gives a step-by-step guide.

I was using TinyProxy and Dansguardian on 9.10, but something broke it when I upgraded to 10.04, so I'm about to give the above a go.

I would recommend also using OpenDNS as a supplement (note that OpenDNS on its own will not be enough if you want content filtering that can't be circumvented by any teenager).

I wish you could just download dansguardian and it gave you a GUI choice to automatically install and configure a proxy.

The alternative of course is to install Ubuntu Christian Edition and it will configure tinyproxy and dansguardian for you.

NOTE:
Just tried it and it works well for me.
The only thing is I would recommend using gksudo instead of just sudo for the gedit commands.

Now, depending on your settings, if you're looking for legit things like "breast cancer", dansguardian may block the results page.  I usually set google search to "Strict", which 99% of the time eliminates the problem.

---

### Post by karthick87 on 2010-06-09
Squid and Dansguardian worked perfectly in ubuntu 9.04 but its not working in lucid.Have you tried..?

---

### Post by drake495 on 2010-06-09
I have not tried it in 10.4 yet, but I did set up such a system on 9.04 in a virtual machine and it worked great.

Here is the tutorial I used. It may have some helpful info.

[http://howtoforge.com/squid-proxy-server-on-ubuntu-9.04-server-with-dansguardian-clamav-and-wpad-proxy-auto-detection]("http://howtoforge.com/squid-proxy-server-on-ubuntu-9.04-server-with-dansguardian-clamav-and-wpad-proxy-auto-detection")

Hope it helps.

---

### Post by morepractice on 2010-08-06
I also tried to Squid but without success. I ended up trying Dan's Guardian with GUI and TinyProxy. If you like to give it a try, see my tutorial on: [http://ubundance.blogspot.com/2010/07/how-to-install-and-setup-dans-guardian.html](http://ubundance.blogspot.com/2010/07/how-to-install-and-setup-dans-guardian.html)

---

