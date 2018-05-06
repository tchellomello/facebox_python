# facebox_python
A python interface to interact with the great [Machinebox/Facebox](https://machinebox.io/).
At the moment I have implemented only two endpoints:
    
    1. `facebox/teach`
    2. `facebox/check`

The reason I have written this interface is because I wanted to teach the facebox multiple people together, and because I wanted to get the result of recognition task `facebox/check` as an image with boxes around the detected faces.

## Usage:
1. Signup for a free account on [Machinebox/Facebox](https://machinebox.io/).
2. Run the docker-image using 
`docker run -p 8080:8080 -e "MB_KEY=$MB_KEY" machinebox/facebox`

Don't forget to add the MB_KEY to your path or `~/.bashrc` file on Linux. Check [documentation](https://machinebox.io/docs/setup/box-key) on how to do that. 

3. from the commandline call either `teach.py` or `check.py`

## Teach endpoint 
To teach the facebox a person/face you have to make a folder with the name of the person. The dataset structure should look like this:
##### Dataset structure
```bash
person_1/
    img1.jpg
    img2.jpg
    ........
person_2/
    image1.png
    image2.png
    ..........
person_3/
    image1.jpeg
    image2.jpeg
    ..........    
..........
```
Allowed extensions for training/teaching are: `.jpg`, `.png` and `.jpeg`

**Remember** with a free license of Machinebox/Facebox you are allowed to teach only 20 faces.

Then just call `teach.py` from the command line 
At the end of the teaching process the file `failed_log.txt` will be written down. The file keep tracks of all failed teaching images/faces. So you can then check why an image has failed to be recognized or taught!


## Check endpoint 
You can the file `check.py --file [filename_path] --save [yes or No]`
#### --file argument: 
you need to specify the iamge/path to the image you want to check 
#### --save argument: 
this is used to save the returned image from the facebox. If you give it `yes` it will save a copy the returned image with recognition boxes on the disk with the name `machinebox-ORIGINAL_FILENAME.jpg`. Or give it `no` and it will only display the returned image without saving it. 

## License

[MIT License](LICENSE)
  