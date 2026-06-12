---
title: "Firefox dialog button on KDE"
date: 2010-04-08
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by lovinglinux on 2010-04-08
It seems they decided to implement some Firefox KDE integration and now the dialog buttons are inverted. This is extremely annoying, because after years clicking the same buttons, my brain already goes to the right to click OK. So I cancel stuff by accident all the time. I image what will happen when I first click OK instead of Cancel.

The userChrome.css modification below can reverse the order of the buttons, but their location is not changing, so they are displayed on the left.

```
.dialog-button-box {-moz-box-direction: reverse !important; -moz-box-pack: right !important;}
```

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=152712&stc=1&d=1270769823[/IMG]

So anyone knows the proper css for putting the buttons on the right, but keeping the order above?

---

