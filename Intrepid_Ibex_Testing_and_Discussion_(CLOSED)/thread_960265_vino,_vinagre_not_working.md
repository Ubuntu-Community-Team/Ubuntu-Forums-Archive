---
title: "vino, vinagre not working"
date: 2008-10-27
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by syxbit on 2008-10-27
i hate it when something really simple doesn't work.

i'm trying to remote in to another intrepid machine (from my intrepid laptop)
both machines have vino and vinagre installed
when i run vinagre on my laptop, and click connect, vinagre instantly closes.

i've loaded 'vino-preferences' and ticked the first two options to allow sharing.
Both machines are connected to the same router, so it shouldn't be a port issue

any ideas?

running from the terminal gives this error
```

The program 'vinagre' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadRequest (invalid request code or no such operation)'.
  (Details: serial 370 error_code 1 request_code 143 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

---

### Post by lean on 2008-10-28
I have the same problem.

The program 'vinagre' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadRequest (invalid request code or no such operation)'.
  (Details: serial 5930 error_code 1 request_code 143 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

---

