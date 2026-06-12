---
title: "ink status for Canon Printers"
date: 2007-11-04
forum: Installation &amp; Upgrades
---

### Post by measekite on 2007-11-04
I am look for a way to check the quantity of ink in a Canon printer.  I did download libinklevel and inkblot.

When I attempt to compile them for Feisty I get so many compile errors of all sorts that only a C programmer could understand.

Does anyone know how to get these compiled and installed.  It would be nice to have a deb to execute taht would work.  The filenames are:

libinklevel-0.7.2     libinklevel     ieee1284-0.2.11 and inkblot-9.99.9


I also have an older version of libinklevel that is supposed to work with a command line ustility called ink.

The command syntax is:
  ink -p usb|parport [-n <portnumber>]

I think my port number is 2.  So I issue, among many different tries

```
ink usb -n 2
```

Nothing worked.  I know I can visually check the carts once a week so I know what to keep an eye on but I really would like to have this.  In windows you get a pop up telling when a cart is low and which one and then another when it is empty.  That is not the case in Linux.  :(

---

### Post by rclark68137 on 2007-11-18
I haven't had much luck with installing inkblot, either.  I did get ink to work, though. I used this command
```
sudo ink -d /dev/usb/lp0
```
It gives me results like this

```
ink v0.4.0 &#65533; 2007 Markus Heinz

Canon iP4200

Black:                         40%
Photoblack:                    40%
Cyan:                          10%
Magenta:                      100%
Yellow:                        40%

```

---

