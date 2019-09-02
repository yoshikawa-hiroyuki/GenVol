# GenVol

## DESCRIPTION
画像データファイル群から、ボリュームデータ生成を生成します。

## USAGE
```
python genVol.py -o outfile [-bb x0 y0 z0 x1 y1 z1] infile1 infile2 ...
```

* `-o outfile`<br>
生成するボリュームデータファイルのパスを指定します。省略はできません。
指定するファイルのフォーマットは、ファイル名の拡張子で判断されます。

  * .vol .fdv : 4D Visualizerボリュームデータファイル
  * .dat .avs : AVSボリュームデータファイル
  * .sph      : V-Sphere/Sphere SPHファイルフォーマット(スカラー)

* `-bb x0 y0 z0 x1 y1 z1`<br>
バウンディングボックスを指定します。
バウンディングボックスは、ボリュームデータが存在する立方体領域の
最小頂点座標`(x0, y0, z0)`および最大頂点座標座標`(x1, y1, z1)`です。
省略した場合は、`(x0, y0, z0) = (0, 0, 0)`、
`(x1, y1, z1) = (IMAX-1, JMAX-1, KMAX-1)`とみなされます。ここで、
`(IMAX, JMAX, KMAX)`は、ボリュームデータのサイズです。

* `infile1 infile2 ...`<br>
入力する画像ファイル群を指定します。指定した画像ファイルの数が
生成されるボリュームデータのKMAXになります。
画像ファイルのフォーマットは、ファイル名の拡張子で判断されます。

  * .png : PNG
  * .ppm : Portable Pixmap
  * .pgm : Portable Graymap
  * .bmp : Microsoft Bitmap
  * .jpg : JPEG/JFIF
  * .gif : GIF
  * .tif : TIFF
  * .dcm : DICOM(非圧縮のみ)

## DEPENDENCY
以下に示すパッケージがPython環境にインストールされている必要があります。

  * Pillow - PIL(Python Imaging Library) fork  https://pillow.readthedocs.io/
  * pydicom (DICOMファイル入力時) https://github.com/pydicom/pydicom/pydicom

