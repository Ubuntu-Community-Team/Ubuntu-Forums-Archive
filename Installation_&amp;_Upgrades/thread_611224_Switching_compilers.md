---
title: "Switching compilers"
date: 2007-11-12
forum: Installation &amp; Upgrades
---

### Post by blackdragon1157 on 2007-11-12
I was doing some things with wine and decided to try out Dev-C++ under it.  Worked well, but thats not the point.  Since Dev doesn't compile Linux executables, I uninstalled it and installed  KDevelop and tried to compile.  I was greeted with "configure: error: C++ compiler cannot create executables
".  I checked my config.log, and found the following:

configure:2469: checking for C++ compiler version
configure:2476: i586-mingw32msvc-c++ --version >&5
/home/dragon/Projects/Illuvien/configure: line 2477: i586-mingw32msvc-c++: command not found

It seems my installation of Dev-C++ messed up my compiler settings.  I have (repeatedly) re-installed gcc g++ and build essential, but to no avail. Help?

---

### Post by arnix on 2007-11-12
can you post here the lines 2460-2480 of your "/home/dragon/Projects/Illuvien/configure" ?

---

### Post by blackdragon1157 on 2007-11-12
```
ac_tool_warned=yes ;;
esac
    CXX=$ac_ct_CXX
  fi
fi

  fi
fi
# Provide some information about the compiler.
echo "$as_me:$LINENO: checking for C++ compiler version" >&5
ac_compiler=`set X $ac_compile; echo $2`
{ (ac_try="$ac_compiler --version >&5"
case "(($ac_try" in
  *\"* | *\`* | *\\*) ac_try_echo=\$ac_try;;
  *) ac_try_echo=$ac_try;;
esac
eval "echo \"\$as_me:$LINENO: $ac_try_echo\"") >&5
  (eval "$ac_compiler --version >&5") 2>&5
  ac_status=$?
  echo "$as_me:$LINENO: \$? = $ac_status" >&5
  (exit $ac_status); }
```

---

### Post by arnix on 2007-11-12
hmm, the thing is here:

ac_compiler=`set X $ac_compile; echo $2`

it is setting the $ac_compiler variable the same value as the $2 variable was (which is the second parameter), need the whole configure file to trace it. But now I must go, if tomorrow won't be solved I will try to help you.

---

