---
title: "Java Printing Issues"
date: 2009-02-16
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by macmasterxiv on 2009-02-16
If you ever have an error printing from a java based program that looks something like this: ```
Exception in thread "AWT-EventQueue-0" java.lang.NullPointerException: null attribute matlab
```
and continues on, then do this:

Specify the page orientation of every printer in cups

System -> Printing

For each printer select Job Options tab and specify Orientation to whatever else instead of "Automatic Rotation".

Thanks to trinh in ubuntu launchpad for the tip above.

---

