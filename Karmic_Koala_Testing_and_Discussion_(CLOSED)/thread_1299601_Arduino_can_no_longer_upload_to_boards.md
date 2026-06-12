---
title: "Arduino: can no longer upload to boards"
date: 2009-10-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by hanzomon4 on 2009-10-24
I've been using the arduino software since I installed karmic and it's worked fine, but now I can't upload anything. I thought it might be my board so I booted into osx and my sketch uploaded fine. So I know it's a Ubuntu problem.

the error message is ```
avrdude: stk500_recv(): programmer is not responding
```

I'm stumped, any ideas?

---

### Post by 23meg on 2009-10-24
> **hanzomon4 said:**
> I've been using the arduino software since I installed karmic and it's worked fine, but now I can't upload anything. I thought it might be my board so I booted into osx and my sketch uploaded fine. So I know it's a Ubuntu problem.

the error message is ```
avrdude: stk500_recv(): programmer is not responding
```

I'm stumped, any ideas?

Which Arduino version (hardware)? Do you attempt to upload right after resetting?

---

### Post by hanzomon4 on 2009-10-24
Atmega168 I believe... I've tried it with a self made board and a Decimilia(sp?). Same result, it works in OSX on my computer so I don't think it's the board and it worked 3 weeks ago. 

At first I was having problems with usb errors but after uninstalling brltty the problem went away. I don't recall having reinstalled in the first place but.. 

I've also tried re-downloading the arduino software and removing the .arduino directory as well as running as root. Could it be a problem with the ftdi driver?

---

### Post by hanzomon4 on 2009-10-24
double post

---

### Post by 23meg on 2009-10-25
Is it a 64-bit installation? If so, try removing the file librxtxSerial.so from the "lib" folder if you haven't. 

It's working fine for me with a Duemilanove.

---

### Post by hanzomon4 on 2009-10-25
Still a no go.. thanks for the help by the way

---

