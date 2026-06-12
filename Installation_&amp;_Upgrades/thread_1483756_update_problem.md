---
title: "update problem"
date: 2010-05-14
forum: Installation &amp; Upgrades
---

### Post by cariso9001 on 2010-05-14
When I  finished update,and I click refresh button.
I got a message from kPackageKit.

This is  the details.

Error Type: 
Error Value: coercing to Unicode: need string or buffer, exceptions.SystemError found
File : /usr/share/PackageKit/helpers/apt/aptBackend.py, line 2216, in 
main()
File : /usr/share/PackageKit/helpers/apt/aptBackend.py, line 2213, in main
run(args, options.single)
File : /usr/share/PackageKit/helpers/apt/aptBackend.py, line 2175, in run
backend.dispatcher(args)
File : /usr/lib/python2.6/dist-packages/packagekit/backend.py, line 699, in dispatcher
self.dispatch_command(args[0], args[1:])
File : /usr/lib/python2.6/dist-packages/packagekit/backend.py, line 606, in dispatch_command
self.refresh_cache(force)
File : /usr/share/PackageKit/helpers/apt/aptBackend.py, line 202, in _locked_cache
func(*args, **kwargs)
File : /usr/share/PackageKit/helpers/apt/aptBackend.py, line 1498, in refresh_cache
format_string(error.message))
File : /usr/lib/python2.6/dist-packages/packagekit/backend.py, line 723, in format_string
txt = unicode(text, encoding, errors='replace')


What can I do now. :confused:

---

