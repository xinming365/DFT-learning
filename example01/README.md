### 晶体硅的计算，包括能带和态密度。
脚本在slurm作业调度系统下使用和提交，脚本内容包括自洽计算，非自洽计算，能带计算和态密度计算。


DOS计算：
STEP 1: scf calculation

STEP 2 : nscf calculation
run a non-self consistent calculation, using a previously computed scf potential.
* has the same prefix and outdir of the previous scf step
* uses a denser k-point mesh than in the previous scf step
* uses the linear tetrahedron method (variable occupations=’tetrahedra’)

STEP 3: DOS calculation
* prefix and outdir are the same of the previous non-scf step
* output is written to file fildos
执行Postprocessing模块中的dos.x命令。dos.x < *.dos.in > *.dos.out

BAND计算
方式一：pw.x ’scf+smearing’         pw.x  ’bands’          plot bands
方式二：pw.x ’scf’ no smearing.     pw.x  ’nscf’        pw.x. ‘bands’       plot bands
