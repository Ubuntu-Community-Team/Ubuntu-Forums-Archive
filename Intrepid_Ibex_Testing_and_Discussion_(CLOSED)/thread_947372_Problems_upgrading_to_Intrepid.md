---
title: "Problems upgrading to Intrepid"
date: 2008-10-14
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by kseise on 2008-10-14
Nautilus:
I got the following error message on a clean install of Hardy upgrading to Intrepid Beta
> Adding client to server's list failed, CORBA error: IDL:omg.org/CORBA/COMM_FAILURE:1.0
Adding client to server's list failed, CORBA error: IDL:omg.org/CORBA/COMM_FAILURE:1.0
Adding client to server's list failed, CORBA error: IDL:omg.org/CORBA/COMM_FAILURE:1.0
Adding client to server's list failed, CORBA error: IDL:omg.org/CORBA/COMM_FAILURE:1.0
Adding client to server's list failed, CORBA error: IDL:omg.org/CORBA/COMM_FAILURE:1.0


Network Manager also says it can not continue.

---

### Post by philinux on 2008-10-14
If you want to try intrepid the easiest way is download the livecd daily build. Especially as you are doing a clean install.

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

---

### Post by linux6994 on 2008-10-14
Was the Hardy full updated? I have upgraded 3 out of 4 machines via network update manager and they are rocking. All apps working fine. All machines run virtualbox w/xp .I just need to update a second laptop still running Hardy,

---

### Post by iponeverything on 2008-10-14
try this:

```

rm ~/.gconfd/saved_state
sudo killall -v -9 gconfd-2

```

---

