---
title: "apt error"
date: 2010-06-07
forum: Installation &amp; Upgrades
---

### Post by akrobert on 2010-06-07
Hello
I have noticed that I have 2 different computers running Ubuntu 10.04 and both of them have the same problem. When the internet is off at the router and it checks for updates it throws the following error.

an internal system error has occured
a problem that we were not expecting has occured

Error Type: <type 'exceptions.TypeError'>
Error Value: coercing to Unicode: need string or buffer, exceptions.SystemError found
  File : /usr/share/PackageKit/helpers/apt/aptBackend.py, line 2216, in <module>
    main()
  File : /usr/share/PackageKit/helpers/apt/aptBackend.py, line 2213, in main
    run(args, options.single)
  File : /usr/share/PackageKit/helpers/apt/aptBackend.py, line 2175, in run
    backend.dispatcher(args)
  File : /usr/lib/python2.6/dist-packages/packagekit/backend.py, line 710, in dispatcher
    self.dispatch_command(args[0], args[1:])
  File : /usr/lib/python2.6/dist-packages/packagekit/backend.py, line 606, in dispatch_command
    self.refresh_cache(force)
  File : /usr/share/PackageKit/helpers/apt/aptBackend.py, line 202, in _locked_cache
    func(*args, **kwargs)
  File : /usr/share/PackageKit/helpers/apt/aptBackend.py, line 1498, in refresh_cache
    format_string(error.message))
  File : /usr/lib/python2.6/dist-packages/packagekit/backend.py, line 723, in format_string
    txt = unicode(text, encoding, errors='replace')

I reinstalled the aptbackend but that didnt seem to help. I looked for an aptbacked.py but cant find that to update or reinstall. Can someone tell me how to fix this?

thanks
Robert

---

### Post by SlidingHorn on 2010-06-07
Doesn't apt require an internet connection? :confused:

---

### Post by lolzwut on 2010-06-07
apt uses internet to check for updates/install software. Internet connection is a must.

---

### Post by akrobert on 2010-06-07
but shouldnt it simply see that one isnt present and check again later until one is active? I never started getting this error until 10.04. In the past it would simply check, no connection it would check again later and when one was present it would go through the checking process...

Robert

---

