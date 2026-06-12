---
title: "X problem in karmic"
date: 2009-10-09
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by diffy on 2009-10-09
Hello,

I've install the beta since it was available and since two days I've some problems with the X server.

When I try to launch Xmoto, or Stellarium, I get an error. Xmoto just stops and stellarium screw up my screen.

Here are the errors I've got : 

```

ptitpc:~$ xmoto
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  135 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  17
  Current serial number in output stream:  17

``````

ptitpc:~$ stellarium 
X Error: BadRequest (invalid request code or no such operation) 1
  Extension:    135 (Uknown extension)
  Minor opcode: 19 (Unknown request)
  Resource id:  0x4b
X Error: BadRequest (invalid request code or no such operation) 1
  Extension:    135 (Uknown extension)
  Minor opcode: 19 (Unknown request)
  Resource id:  0x4b
X Error: BadRequest (invalid request code or no such operation) 1
  Extension:    135 (Uknown extension)
  Minor opcode: 14 (Unknown request)
  Resource id:  0x4b
X Error: BadRequest (invalid request code or no such operation) 1
  Extension:    135 (Uknown extension)
  Minor opcode: 19 (Unknown request)
  Resource id:  0x4b

```

Otherwise I want to thanks all the ubuntu development team because you're doing a very good job on this release, karmic is awesome !

David

---

