---
title: "system-config-printer cannot connect to localhost"
date: 2009-10-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by azelter on 2009-10-16
I did a clean install of karmic beta yesterday and updated everything as of Oct 15th. When trying to install a printer with system-config-printer on the standard menu I got nothing after clicking the 'new' button.
The cups access log showed "POST / HTTP/1.1" 200 8421 CUPS-Get-Devices - and nothing more. The cups error log showed: E [16/Oct/2009:09:28:31 -0700] [cups-driverd] Bad driver information file "/usr/share/cups/drv/sample.drv"!

The printer (a network Xerox) detected and installed perfectly using the [http://localhost:631/](http://localhost:631/) interface.

Once the printer was installed it showed up in system-config-printer, which then let me set it as the system default.

I have no idea why system-config-printer did not work, but wanted to post my experience in case others are having the same problem.

---

