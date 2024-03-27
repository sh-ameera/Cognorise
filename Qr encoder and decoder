import qrcode as qr
import cv2 as cv

def generate_qr(data, filename):
    q = qr.QRCode(
        version=1,
        error_correction=qr.constants.ERROR_CORRECT_L,
        box_size=10,
        border=4,
    )
    q.add_data(data)
    q.make(fit=True)

    img = q.make_image(fill_color="black", back_color="white")
    img.save(filename)

def read_qr(filename):
    img = cv.imread(filename)

    detector = cv.QRCodeDetector()

    data, bbox, _ = detector.detectAndDecode(img)

    if bbox is not None:
        return data
    else:
        return "QR code not detected or cannot be decoded"

def main():
    while True:
        print("\n1. Generate QR code")
        print("2. Read QR code")
        print("3. Exit")
        choice = input("Enter your choice (1/2/3): ")

        if choice == "1":
            data = input("Enter the data to encode: ")
            filename = input("Enter the filename to save the QR code image: ")
            generate_qr(data, filename)
            print("QR code generated successfully!")
        elif choice == "2":
            filename = input("Enter the filename of the QR code image to read: ")
            data = read_qr(filename)
            print("Decoded data:", data)
        elif choice == "3":
            print("Exiting the program.")
            break
        else:
            print("Invalid choice. Please enter 1, 2, or 3.")

if __name__ == "__main__":
    main()
