---
title: "can't install linuxdcpp"
date: 2007-06-09
forum: Installation &amp; Upgrades
---

### Post by superstar on 2007-06-09
Hello!
I'm trying to install linux dcpp and when i run "sudo scons" i get this:

Checking for iconv(0, (const char **)0, 0, (char**)0, 0) in C library iconv... no
<type 'exceptions.TypeError'>: Directory /home/hello/linuxdcpp/linuxdcpp found where file expected.:
  File "/home/hello/linuxdcpp/SConstruct", line 192:
    SConscript('linux/SConstruct', exports='env', build_dir='build/gui', duplicate=0)])
  File "/usr/lib/scons/SCons/Environment.py", line 188:
    return apply(self.builder, (self.env, target, source) + args, kw)
  File "/usr/lib/scons/SCons/Builder.py", line 615:
    return self._execute(env, target, source, OverrideWarner(kw), ekw)
  File "/usr/lib/scons/SCons/Builder.py", line 794:
    return BuilderBase._execute(self, env, target, final_sources, overwarn)
  File "/usr/lib/scons/SCons/Builder.py", line 567:
    tlist, slist = self._create_nodes(env, target, source)
  File "/usr/lib/scons/SCons/Builder.py", line 522:
    tlist = env.arg2nodes(target, target_factory)
  File "/usr/lib/scons/SCons/Environment.py", line 354:
    v = node_factory(self.subst(v, raw=1))
  File "/usr/lib/scons/SCons/Node/FS.py", line 1120:
    return self.Entry(name, directory, create, File)
  File "/usr/lib/scons/SCons/Node/FS.py", line 1107:
    return self._doLookup(klass, name, directory, create)
  File ".../SCons/Memoizer-cache_get-lambda<_doLookup>", line 4:
    None
  File "/usr/lib/scons/SCons/Memoize.py", line 287:
    rval = cdict[ckey] = apply(func, args, kw)
  File "/usr/lib/scons/SCons/Node/FS.py", line 1037:
    result.diskcheck_match()
  File "/usr/lib/scons/SCons/Node/FS.py", line 1728:
    "Directory %s found where file expected.")
  File "/usr/lib/scons/SCons/Node/FS.py", line 351:
    raise TypeError, errorfmt % path

what shall i do.where can i get the iconv libraries from?and how?
thanx

---

### Post by madmetal on 2007-06-10
if you want to easily install linux dcpp you can try automatix ;)


UAResolved.

---

### Post by stevensheehy on 2007-06-14
The error isn't that you're missing iconv. The actual error listed is:

Directory /home/hello/linuxdcpp/linuxdcpp found where file expected

It looks like you have a subdirectory called 'linuxdcpp' inside the main linuxdcpp folder. The executable is also called 'linuxdcpp', so having this subdir causes it to fail. Short answer:

rm -rf /home/hello/linuxdcpp/linuxdcpp/

---

