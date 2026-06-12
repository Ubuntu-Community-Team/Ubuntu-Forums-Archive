---
title: "upgraded gutsy-hardy--sound issues"
date: 2008-05-04
forum: Installation &amp; Upgrades
---

### Post by stubblepoo on 2008-05-04
right here is the situation. having upgraded i realised my login sound wasnt running. the beep at the login screen however still runs. in system-->preferences-->sound all the test sounds on the first tab work, however no other sound files or internet or system sounds do work. at wits end help please.

---

### Post by Pumalite on 2008-05-04
What's the result of typing 'alsamixer' in your Terminal?

---

### Post by stubblepoo on 2008-05-04
i get a really nice graphical volume thing. i put everything on max and when i played a sound clip it worked once than stopped playing. i could post a screenshot if that would be helpful?

---

### Post by Pumalite on 2008-05-04
No. Your card is recognized, the module is loaded and alsamixer is working. These must be debris from an upgrade.

---

### Post by stubblepoo on 2008-05-04
i think i have fixed it, thanks

---

### Post by Pumalite on 2008-05-04
You are welcome, but how did you fix it, so everyone can benefit here?

---

### Post by stubblepoo on 2008-05-05
on alsamixer it had reduced mst things to zero, i whacked them to halfway and sound was back

---

### Post by stubblepoo on 2008-05-05
not fully fixed. in preferences-sounds the login and logout sounds still do not respond, everything else does.

---

