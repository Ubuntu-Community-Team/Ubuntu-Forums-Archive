---
title: "[SOLVED] configuration error - unknown item 'FAIL_DELAY' (notify administrator)"
date: 2007-09-28
forum: Installation &amp; Upgrades
---

### Post by cmnorton on 2007-09-28
After upgrading to 7.04, I got this message. I was telnet-ing  into the system:

Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
Ubuntu 7.04
configuration error - unknown item 'FAIL_DELAY' (notify administrator)

Nothing bad happens. I am just wondering about the message and how I might clear it.

I upgraded telnetd; it refused all connections; I rebooted; was still getting this error, and then commented out FAIL_DELAY in login.defs. Problem is solved.


#
# Delay in seconds before being allowed another attempt after a login failure
#
#FAIL_DELAY             3

---

