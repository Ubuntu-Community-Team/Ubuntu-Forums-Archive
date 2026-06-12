---
title: "Synaptic Package Manager and Python"
date: 2011-01-17
forum: Installation &amp; Upgrades
---

### Post by Guidobot on 2011-01-17
I installed the IDLE Python editor (3.1) using Synaptic Package Manager, which appears to be working fine.

I then installed NumPy and BioPython packages likewise, which appear to have been installed to folders in  /usr/share/pyshared/...

However, when I try to import from an IDLE session I get the error attempting the smoketest cmd:
from Bio.Seq import Seq
...
...ImportError: No module named Bio.Seq

Is there something I need to do to get Python (IDLE) to locate these packages?

---

### Post by Guidobot on 2011-01-18
This issue was simply that these packages are not available (yet) for Python 3.1.

The solution was to additionally install the 2.6 version of Python IDLE.

---

