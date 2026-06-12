---
title: "pure data problems pd"
date: 2007-05-09
forum: Installation &amp; Upgrades
---

### Post by prolapsedisk on 2007-05-09
I have pd in feisty, and for the life of me i can't get it to make any sound at all. 

cat /dev/urandom > /dev/dsp works
sound-juicer works
startup sounds work

running pd, there's a serious lag, and opening pd patches takes a long time before the corresponding window displays, and the patch doesn't start at all.

Has anyone got a suggestion?

---

### Post by timredfern on 2007-10-31
try: 

pd -noadc

---

