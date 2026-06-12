---
title: "OpenDNS Automatic Update Configuration under Karmic"
date: 2009-10-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Kincaid3580 on 2009-10-26
Spent about three hours figuring this out. For those of you who are using OpenDNS (much faster than my ISP's (Comcast's) DNS servers) here is a simple way to get this to work:

First, install the ddclient from the Karmic repositories by your favorite method.

Then, paste the following into the ddclient.conf file in /etc/:

##
## OpenDNS.com account-configuration
##
ssl=yes # use ssl-support
use=web, web=whatismyip.org

server=updates.opendns.com
protocol=dyndns2
login=USERNAME
password=PASSWORD
YOUR_NETWORK_NAME

Obviously, replace USERNAME, PASSWORD and YOUR_NETWORK_NAME with the correct settings from your OpenDNS account.

Using your favorite service manager tool (I like chkconfig myself) verify the service is there, set the runlevels you would wish it to run under (usually 2-5 if not already set) and start/restart the service.

Much easier when you check the repositories *first*!! /facepalm

Let me know if this helps or if you encounter any issues.

---

### Post by Kincaid3580 on 2009-10-26
Just found an issue with the routine.. working on updating it now.. will repost when I get it fixed.

---

### Post by Kincaid3580 on 2009-10-26
Fixed in original post...

---

### Post by Kincaid3580 on 2009-10-26
Fixed in main post...

---

