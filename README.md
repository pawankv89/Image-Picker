
Image-Picker
=========

## iOS Image-Picker help to capture image from Camera or Gallery
------------
 Added Some screens here.
 
[![](https://github.com/pawankv89/Image-Picker/blob/master/images/screen_1.png)]
[![](https://github.com/pawankv89/Image-Picker/blob/master/images/screen_2.png)]
[![](https://github.com/pawankv89/Image-Picker/blob/master/images/screen_3.png)]



## Usage
------------
 
Integration Steps

```swift

//MARK: - Open the camera
func openCamera(){
if(UIImagePickerController .isSourceTypeAvailable(UIImagePickerController.SourceType.camera)){
imagePicker.sourceType = UIImagePickerController.SourceType.camera
//If you dont want to edit the photo then you can set allowsEditing to false
imagePicker.allowsEditing = true
imagePicker.delegate = self
self.present(imagePicker, animated: true, completion: nil)
}
else{
let alert  = UIAlertController(title: "Warning", message: "You don't have camera", preferredStyle: .alert)
alert.addAction(UIAlertAction(title: "OK", style: .default, handler: nil))
self.present(alert, animated: true, completion: nil)
}
}

//MARK: - Choose image from camera roll

func openGallary(){
imagePicker.sourceType = UIImagePickerController.SourceType.photoLibrary
//If you dont want to edit the photo then you can set allowsEditing to false
imagePicker.allowsEditing = true
imagePicker.delegate = self
self.present(imagePicker, animated: true, completion: nil)
}

```

There is a sample function in ViewController that you can simply call. 

```swift
//MARK: - UIImagePickerControllerDelegate (Swift 4.2) Used
func imagePickerController(_ picker: UIImagePickerController, didFinishPickingMediaWithInfo info: [UIImagePickerController.InfoKey : Any]) {

    var selectedImage: UIImage?

    if let editedImage = info[UIImagePickerController.InfoKey.editedImage]! as? UIImage {
       selectedImage = editedImage
       self.userProfileImageView.image = selectedImage!

} else if let originalImage = info[UIImagePickerController.InfoKey.originalImage]! as?        UIImage  {
        selectedImage = originalImage
        self.userProfileImageView.image = selectedImage!
}

      //Dismiss the UIImagePicker after selection
      picker.dismiss(animated: true, completion: nil)
}

func imagePickerControllerDidCancel(_ picker: UIImagePickerController) {
    picker.isNavigationBarHidden = false
    self.dismiss(animated: true, completion: nil)
}
```


## License

This code is distributed under the terms and conditions of the [MIT license](LICENSE).

## Change-log

A brief summary of each this release can be found in the [CHANGELOG](CHANGELOG.mdown). 
