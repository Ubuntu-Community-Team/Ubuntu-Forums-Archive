---
title: "Cuda with Theano"
date: 2011-06-09
forum: Installation &amp; Upgrades
---

### Post by zermelozf on 2011-06-09
Hello,

I am trying to install the theano library as specified on [http://deeplearning.net/software/theano](http://deeplearning.net/software/theano). I would like to run code on the GPU.
The installation seems to be incomplete though.
I downloaded the cuda drivers and toolkit from the nvidia site and installed them.
When I try to run the example thing.py available at [http://deeplearning.net/software/theano/tutorial/using_gpu.html#setting-up-cuda](http://deeplearning.net/software/theano/tutorial/using_gpu.html#setting-up-cuda) using GPU and float32, I have an the console prompts an incredibly large number of warning, and finally displays the following excption:
```
560 PyMODINIT_FUNC init0348d714aff443efa17990e312b68180(void){
561    import_array();
562    (void) Py_InitModule("0348d714aff443efa17990e312b68180", MyMethods);
563 }
564 
Traceback (most recent call last):
  File "CPUvsGPU.py", line 16, in <module>
    f = function([], T.exp(x))
  File "/usr/local/lib/python2.6/dist-packages/theano/compile/function.py", line 105, in function
    allow_input_downcast=allow_input_downcast)
  File "/usr/local/lib/python2.6/dist-packages/theano/compile/pfunc.py", line 270, in pfunc
    accept_inplace=accept_inplace, name=name)
  File "/usr/local/lib/python2.6/dist-packages/theano/compile/function_module.py", line 1109, in orig_function
    fn = Maker(inputs, outputs, mode, accept_inplace = accept_inplace).create(defaults)
  File "/usr/local/lib/python2.6/dist-packages/theano/compile/function_module.py", line 984, in create
    _fn, _i, _o = self.linker.make_thunk(input_storage = input_storage_lists)
  File "/usr/local/lib/python2.6/dist-packages/theano/gof/link.py", line 321, in make_thunk
    output_storage = output_storage)[:3]
  File "/usr/local/lib/python2.6/dist-packages/theano/gof/cc.py", line 1184, in make_all
    output_storage = node_output_storage)
  File "/usr/local/lib/python2.6/dist-packages/theano/gof/cc.py", line 780, in make_thunk
    cthunk, in_storage, out_storage, error_storage = self.__compile__(input_storage, output_storage)
  File "/usr/local/lib/python2.6/dist-packages/theano/gof/cc.py", line 729, in __compile__
    output_storage)
  File "/usr/local/lib/python2.6/dist-packages/theano/gof/cc.py", line 1043, in cthunk_factory
    module = get_module_cache().module_from_key(key=key, fn=self.compile_cmodule)
  File "/usr/local/lib/python2.6/dist-packages/theano/gof/cmodule.py", line 429, in module_from_key
    module = fn(location=location)  # WILL FAIL FOR BAD C CODE
  File "/usr/local/lib/python2.6/dist-packages/theano/gof/cc.py", line 972, in compile_cmodule
    preargs=preargs)
  File "/usr/local/lib/python2.6/dist-packages/theano/sandbox/cuda/nvcc_compiler.py", line 228, in nvcc_module_compile_str
    raise Exception('nvcc return status', p.returncode, 'for cmd', ' '.join(cmd))
Exception: ('nvcc return status', 1, 'for cmd', '/usr/local/cuda/bin/nvcc -shared -g --maxrregcount=32 -O3 -m32 -Xcompiler -Wno-write-strings,-fno-math-errno,-Wno-unused-label,-Wno-unused-variable,-fPIC,-m32 -Xlinker -rpath,/usr/local/cuda/lib -Xlinker -rpath,/usr/local/cuda/lib64 -I/usr/home/arnaud/.theano/compiledir_Linux-2.6.32-25-generic-i686-with-Ubuntu-10.04-lucid--2.6.5/cuda_ndarray -I/usr/local/cuda/include -I/usr/lib/python2.6/dist-packages/numpy/core/include -I/usr/include/python2.6 -I/usr/local/lib/python2.6/dist-packages/theano/sandbox/cuda -o /usr/home/arnaud/.theano/compiledir_Linux-2.6.32-25-generic-i686-with-Ubuntu-10.04-lucid--2.6.5/tmptvT12v/0348d714aff443efa17990e312b68180.so mod.cu /usr/home/arnaud/.theano/compiledir_Linux-2.6.32-25-generic-i686-with-Ubuntu-10.04-lucid--2.6.5/tmptvT12v/../cuda_ndarray/cuda_ndarray.so -L/usr/local/cuda/lib -L/usr/home/arnaud/.theano/compiledir_Linux-2.6.32-25-generic-i686-with-Ubuntu-10.04-lucid--2.6.5/cuda_ndarray -L/usr/local/cuda/lib -L/usr/local/cuda/lib64 -L/usr/lib -lpython2.6 -lcudart -lcublas')

```Has anyone already seen this error and knows what might be causing it?
I am usinf ubuntu 10.04 and a nVidia Corporation G86 [GeForce 8500 GT].
Thank you for your help.

---

